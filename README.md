# QLink - Game and Simulation Engine — Linux PCVR for Quest 3 (project preview)
<br>

## Videos

| Race Track Test & Soft-Body Damage | Bullet Penetration & Dynamic Surface | Early Build: Shoothouse Run |
| :---: | :---: | :---: |
| [![Race Track](https://img.youtube.com/vi/eQ5rVYOXnUo/mqdefault.jpg)](https://www.youtube.com/watch?v=eQ5rVYOXnUo) | [![Bullet Penetration](https://img.youtube.com/vi/fvKUhI66D1c/mqdefault.jpg)](https://www.youtube.com/watch?v=fvKUhI66D1c) | [![Shoothouse](https://img.youtube.com/vi/1Sw6SI0MJxI/mqdefault.jpg)](https://www.youtube.com/watch?v=1Sw6SI0MJxI) |

**qlink** is an independent research project that brings wired PC VR to Linux for the Meta Quest 3. The PC renders the whole VR world, including the home, the avatar and its body IK, the applications and the final frames. It streams the result over the USB cable to the stock Quest Link receiver. Nothing is installed on the headset, and no custom Quest app is involved.

- **No Quest Link PC app.** qlink runs on Linux without Meta's Quest Link (Oculus) PC software. The Linux host talks to the stock Link receiver on the headset directly.
- **The PC world is the Link home.** The headset shows a PC-rendered world in place of the usual Link home. The desktop can play the same world in 2D. A new shared simulation is being integrated; the headset path has not switched to it yet.
- **Goal: replace the Link app completely.** A future OpenXR runtime is meant to let Steam and other VR games start through qlink, and return to the home afterwards (see the [roadmap](docs/ROADMAP.md)). This is planned, not available yet.

This repository is a **public preview**. It shows progress through renders, videos and short write-ups. The source code, internal research notes and protocol documentation are not published here.

> Status: experimental research, not a product. It has been tested on one Quest 3 with one PC (RTX 3080, Linux). Not affiliated with or endorsed by Meta.

> [!IMPORTANT]
> **Very early development version.** qlink is under active development. Work is focused on making the full path run reliably and on improving it step by step. Many parts are incomplete, and things change quickly.
>
> **Renders are updated regularly**, so this repository shows how the project progresses over time. See the [progress log](docs/PROGRESS.md).
>
> **Test versions and contributors:** there are no public builds yet. Later, test versions and collaboration will be offered **by invitation**. If you are interested, open a [tester interest](../../issues/new?template=tester-interest.yml) or [offer to help](../../issues/new?template=offer-help.yml) issue.
>
> **Ideas and feedback are welcome** through [issues](../../issues/new/choose) and [Discussions](../../discussions). See [CONTRIBUTING.md](CONTRIBUTING.md).

![Island home world](media/images/island-shore.jpg)

## Highlights

- **Native USB streaming to the stock Link receiver.** On one Quest 3, the Linux host completed the session handshake and started the stock Link runtime. It streamed a PC-rendered world as 4128 × 2208 side-by-side HEVC at 72 Hz while receiving head, controller and optical-hand tracking. One bounded run displayed frames for 120 s.
- **The PC does all the rendering.** Vulkan is the current default and draws at full headset resolution with in-process HEVC encoding; its current headset appearance and cadence still need a live repeat. A multithreaded CPU renderer remains available as fallback.
- **Own engine and worlds.** Built-in worlds include an island with shallow-water surf, an underwater reef, weather and grass and palms you can touch. There is also a race circuit with a drivable car and a shooting range with a two-storey, six-room training house.
- **Full-body avatars.** Anatomical characters with 49 joints, all ten fingers animated, faces with expressions, clothing layers, and IK driven by head and hand tracking.
- **Player health simulation.** Projectile paths are traced through body regions and internal organs. Fractures, bleeding, breathing, consciousness, movement, weapon grip and death all follow from the hits.
- **Physical simulation.** Firearm mechanics, material damage (bullet holes, shoot-through walls, breaking timber, ricochets and fragments), vehicle dynamics and crash deformation, shallow-water surf, foliage contact and ragdolls.
- **Tooling.** A desktop console and world editor, a character studio, plus Animation Lab, Sound Lab, Crash Lab and a scripted clip maker.

## Simulation and multiplayer progress

The project now has a fixed-tick Rust simulation with an entity component system, rigid-body physics and shared rules for players, NPCs, items, weapons, injuries and vehicles. The desktop console enables the new simulation path by default. Its shooting-range integration is still being completed: some course and player state remains in the older home code. The native headset session still uses that older path. [Simulation details](docs/SIMULATION.md) and the [architecture](docs/ARCHITECTURE.md) show the current split.

A server-authoritative game network can replicate VR and desktop player inputs and simulation state. It has passed synthetic packet-loss tests and local UDP loopback tests. There has been no validated live multiplayer session between PCs or with a headset. Secure connections, interest management and a persistent shared world are future work. The game network is separate from the Quest Link USB connection.

## Already in the PC game

These features run in the PC build or have passed offline PC tests and render reviews. Their appearance and controls in the current headset build still need separate validation.

- **Places to explore:** a generated island with beach, surf, underwater reef, swimming, rain, clouds, grass and touch-reactive plants; a race circuit; and a shooting range with targets, a shooting house and a two-storey, six-room training house.
- **Training-house encounters:** shuffled hostage and armed-suspect scenarios, backup gunmen, cover-aware return fire, wound reactions, dropped weapons, room progression and a saved score. The house has stairs, furnished rooms and a fire-escape route.
- **Weapons and interaction:** a P9 pistol and M4-style carbine with magazines and fire controls; loose cartridges, pickup and inventory; a P9 flashlight and red-dot sight; muzzle light, recoil and shot view shake. A desktop player can use bandages to stop bleeding in a reachable body region.
- **Physical consequences:** material-dependent bullet marks, shoot-through plywood, falling timber, ricochets and fragments; organ injuries, bleeding, fractures and visible wounds; car crashes that bend panels and damage tyres; sliding tyre marks.
- **Players and presentation:** full-body IK, animated fingers, facial expressions, clothing with protection and wet or damaged appearance, held-weapon animation, sun shadows and PC-side footsteps and weapon/vehicle sounds.
- **PC tools:** the desktop console and world editor, a categorized Asset Viewer, Character Studio, Animation Lab, Weapon Lab, Sound Lab, Cloth Lab, Crash Lab and scripted scene export.

The [feature inventory](docs/FEATURES.md) separates offline, live and planned status for each area.

## Gallery

All images below come from the project's **Vulkan GPU renderer** (RTX 3080). They are unedited offline renders, not concept art. They show the state when captured; later world materials and the training house have changed. These images do not demonstrate the current headset or multiplayer path.

### Island world

| | |
| --- | --- |
| ![Island overview](media/images/island-overview.jpg) | ![Palms and grass](media/images/island-palms.jpg) |
| Overview with simulated surf | Palms, plants and grass that react to touch |
| ![Beach](media/images/island-beach.jpg) | ![Shallow water](media/images/island-water.jpg) |
| Beach and wet sand | Refracting shallow water, foam and run-up |

**Ocean video:** [surf and water motion over 4 s](media/videos/island-ocean.mp4) · [beach view](media/videos/island-beach.mp4)

### Characters

![Character views](media/images/character-views.jpg)

| | |
| --- | --- |
| ![Face](media/images/character-face.jpg) | ![GPU-skinned crowd](media/images/gpu-skinned-crowd.jpg) |
| Anatomical face with eyes, teeth and expression rig | Eight full-detail bodies skinned on the GPU in one frame |

### Animation

| Clip | Video |
| --- | --- |
| Pistol reload: magazine change and slide rack | [pistol-reload.mp4](media/videos/pistol-reload.mp4) |
| Pistol draw and aim, full body | [pistol-draw-aim.mp4](media/videos/pistol-draw-aim.mp4) |
| Walk cycle with foot locking | [walk-cycle.mp4](media/videos/walk-cycle.mp4) |

Clips are rig-independent `.qlanim` files. They are edited in Animation Lab and can be recorded from the wearer's PC-solved pose in VR.

### Shooting range and race circuit

| | |
| --- | --- |
| ![Range lane](media/images/range-lane.jpg) | ![Range counter](media/images/range-counter.jpg) |
| Range lanes with distance boards and targets | Shooting counter with pistol and magazines |
| ![Shoothouse](media/images/range-shoothouse.jpg) | ![Earlier SWAT course](media/images/swat-course-rooms.jpg) |
| Shoothouse | Earlier four-room course, since replaced by a two-storey training house |
| ![Race start line](media/images/race-start-line.jpg) | ![Race hillcrest](media/images/race-hillcrest.jpg) |
| Race circuit start line | Circuit hillcrest with the drivable car |

### Scripted scene

[**Scripted range clip (MP4, 5 s)**](media/videos/scripted-range-clip.mp4): a staged scene made with the clip maker and rendered on the GPU. A scripted shot event drives the health system, which produces the hit reaction and the fall.

![Clip frames](media/images/clip-sheet.jpg)

This is a scripted demonstration. It is not a headset capture and does not show autonomous NPC behaviour.

## Read more

- [Features](docs/FEATURES.md): what exists today, and how far each part is validated
- [Simulation and health](docs/SIMULATION.md): the shared simulation, multiplayer boundary, health, damage, vehicles, water and physics
- [Architecture](docs/ARCHITECTURE.md): how the pieces fit together at a high level
- [Progress log](docs/PROGRESS.md): development timeline
- [Roadmap](docs/ROADMAP.md): where the project is heading

## Principles

- **Clean-room.** Behaviour is observed and documented independently. No proprietary runtime code, drivers, SDK headers or assets are copied or redistributed.
- **No circumvention.** No bypassing of authentication, entitlement, DRM or encryption, and no collection of credentials or account data.
- **Evidence first.** A capability is claimed only after a dated test under stated conditions. Offline and synthetic results are labelled as such.

---

*Preview updated 2026-10-09.*
