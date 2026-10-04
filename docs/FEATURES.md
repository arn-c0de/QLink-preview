# Features

State as of 2026-10-04. Each row says how far the feature is validated:

- **Live (1 device):** observed working on one Quest 3 in a bounded session.
- **Offline:** passes automated tests and inspected PC renders, but has not been confirmed in the headset.
- **Planned:** not implemented yet.

## Streaming and runtime

| Feature | State |
| --- | --- |
| USB connection to the stock Quest Link receiver (no headset app) | Live (1 device) |
| Session handshake and stock Link runtime start | Live (1 device) |
| HEVC video, 4128 × 2208 side by side at 72 Hz | Live (1 device); one run of 120 s |
| Head tracking | Live (1 device) |
| Controllers (pose, trigger, face buttons) | Partly live; stick and grip mapping offline only |
| Optical hand tracking (joints, pinch, grip) | Live transport; interaction feel not yet confirmed |
| Full-resolution Vulkan renderer with in-process HEVC encoding | Offline (decodable stream, no headset run yet) |
| Disconnect, reconnect and sleep recovery | Partial; one cable reconnect observed |
| Headset audio and haptics | Planned |
| OpenXR runtime for standard VR apps | Planned |

## Worlds

| Feature | State |
| --- | --- |
| Island: terrain generated from a seed, sand-to-grass blending, photographic CC0 ground textures | Offline |
| Shallow-water surf with run-up, foam, spray and wet sand | Offline |
| Underwater reef, kelp, fish, swimming and diving | Offline |
| Weather: cloud layers, storm cycle, rain and wet ground | Offline |
| Palms, plants and grass that bend under hands and bodies | Offline |
| Race circuit with a drivable car, opening doors and tyre marks | Offline |
| Shooting range with a four-room training course and a saved score | Offline |
| Sun shadows from the player, props and vehicles | Offline |

## Characters

| Feature | State |
| --- | --- |
| Anatomical avatar, 49 joints, all ten fingers animated | Offline |
| Full-body IK from head and hand tracking | Live input; appearance still under review |
| Faces: blinks, gaze, expressions, hit reactions | Offline |
| Clothing layers with wet and damage appearance | Offline (early proxies) |
| Character studio: any mesh or object can become a character | Offline |
| Animation clips, Animation Lab editor, VR motion recording | Offline (VR recording path tested synthetically) |

## Simulation

| Feature | State |
| --- | --- |
| Data-driven firearm simulation (pistol, magazines, loose cartridges, accessories) | Offline |
| Material damage: bullet holes, shoot-through walls, breaking timber, ricochets, fragments | Offline |
| Player health: traced organ hits, fractures, bleeding, breathing, consciousness, grip, death | Offline |
| Injury rendering on CPU and GPU: entry/exit wounds, blood on skin and clothing, ragdolls | Offline |
| Vehicle crash deformation and damaged-tyre behaviour | Offline |
| Procedural sound for the car engine and the pistol (desktop only) | Offline |

See [Health and simulation](SIMULATION.md) for details.

## Tools

| Tool | Purpose |
| --- | --- |
| Desktop console | Joins the same world as the headset, provides desktop players and debug views |
| World editor | Places objects, sculpts surfaces, saves worlds as editable JSON |
| Character studio | Builds and inspects characters and outfits |
| Animation Lab | Edits, cleans up and records animation clips |
| Sound Lab | Catalogues, renders and reviews every generated sound |
| Crash Lab | Sweeps crash speeds, angles and obstacles for vehicle damage |
| Clip maker | Renders scripted scenes to MP4 from a JSON timeline |
