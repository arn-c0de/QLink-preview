# Architecture

A high-level view. Protocol details and the source code are not part of this preview.

## Data flow

```mermaid
flowchart LR
    subgraph PC["Linux PC"]
        W["World and game state<br/>Home to shared simulation cutover"]
        R["Renderer<br/>Vulkan default / CPU fallback"]
        E["HEVC encoder"]
        T["Transport<br/>userspace USB"]
        D["Desktop console<br/>and editors"]
        N["Game network<br/>server-authoritative, experimental"]
        W --> R --> E --> T
        W <--> D
        W <--> N
    end
    subgraph Q["Quest 3 (stock software)"]
        L["Stock Link receiver"]
    end
    T -- "video frames" --> L
    L -- "head, controller and hand tracking" --> T
    T -. "poses" .-> W
```

1. The headset sends head, controller and optical-hand tracking to the PC over USB.
2. The PC updates the world, solves full-body IK for the wearer and renders both eyes.
3. Frames are encoded as HEVC and sent back to the stock receiver, which displays them.
4. The desktop console and editors view and edit the same live world as a 2D window.
5. The game network, when used, exchanges player inputs and simulation state with other PCs. It is separate from the headset USB stream.

## Design choices

- **The PC owns everything.** The home, avatars, applications and final frames are computed on the PC, so the headset only displays and tracks.
- **Userspace and least privilege.** USB access runs in userspace and needs no kernel driver.
- **Rust throughout.** The host, engine, renderer and tools are written in Rust. Unsafe code is limited to FFI and USB boundaries.
- **Layered workspace.** Separate crates for math, transport, encoding, tracking, rendering, worlds, avatars, health, firearms, deformation, animation and tools. An automated check keeps layer dependencies one-directional.
- **Data, not code.** Worlds, props, weapons, clothing, sounds and animation clips are versioned JSON or clip files that people and agents can edit.
- **Deterministic and replayable.** Transport and session logic are tested against synthetic replays. Live hardware is an opt-in dependency of the tests.
- **Explicit clocks.** Monotonic timestamps with explicit clock domains, so pose prediction and frame pacing stay measurable.

## Shared simulation cutover

The selected game model is a fixed 60 Hz Rust simulation with an entity component system. It handles players, NPCs, items, physical bodies, injuries, weapons and vehicles. Its server is authoritative for shared outcomes; VR and desktop players use the same kind of simulated entity with different input sources.

The desktop console enables this simulation path by default. The shooting range still has some gameplay state in the older home implementation, so the cutover is incomplete. The native Quest Link session leaves the new path disabled until integration, visual review, performance measurement and a live headset run pass. Replication has been checked with synthetic packet loss and local UDP loopback; a live multi-PC session is still open.

## Rendering

- **Vulkan renderer (current default):** renders at the full 4128 × 2208 and encodes HEVC in-process with Vulkan Video, without an external encoder process. Offline output matches the CPU reference; the current default has not had a follow-up headset run.
- **CPU renderer (selectable fallback):** multithreaded rasterizer with textured terrain, water, weather, skinned avatars and projected sun shadows. Its older offline sample at 2064 × 1104 measured about 8–10 ms median.
- **Desktop views:** OpenGL in the editor, sharing a shader library with the headset renderer.
