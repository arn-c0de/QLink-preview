# Features

State as of 2026-10-09. Each row says how far the feature is validated:

- **Live (1 device):** observed working on one Quest 3 in a bounded session.
- **Offline:** passes automated PC tests and, for visual features, inspected PC renders; current headset behavior remains unconfirmed.
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
| Vulkan as the default renderer, CPU as selectable fallback | Implemented; current default needs a follow-up headset run |
| Disconnect, reconnect and sleep recovery | Partial; one cable reconnect observed |
| Headset audio and haptics | Planned |
| OpenXR runtime for standard VR apps | Planned |

## Worlds

| Feature | State |
| --- | --- |
| Island: terrain generated from a seed, sand-to-grass blending, photographic CC0 ground textures | Offline |
| Island beach, wet sand and surf that shoals, breaks, foams and runs up the shore | Offline |
| Underwater reef, kelp, fish, swimming and diving | Offline |
| Weather: cloud layers, storm cycle, rain and wet ground | Offline |
| Palms, plants and grass that bend under hands and bodies | Offline |
| Race circuit with a drivable car, opening doors and tyre marks | Offline |
| Shooting range with distance targets, moving targets, pickup supplies and shoot-through props | Offline |
| Two-storey, six-room training house with furnished rooms, stairs and fire escape | Offline |
| Shuffled hostage and armed-suspect encounters, backup gunmen and saved score | Offline |
| Armed figures return fire around cover, reload, react to hits and drop weapons | Offline |
| Sun shadows from the player, props and vehicles | Offline |
| Range and race ground materials, window sun patches and flashlight-lit rooms | Offline PC render reviews; headset review open |

## Characters

| Feature | State |
| --- | --- |
| Anatomical avatar, 49 joints, all ten fingers animated | Offline |
| Full-body IK from head and hand tracking | Live input; appearance still under review |
| Faces: blinks, gaze, expressions, hit reactions | Offline |
| Clothing layers with wet and damage appearance | Offline (early proxies) |
| Garment protection that reduces projectile energy and weakens after hits | Offline |
| Wound reactions, reachable wound pressure and guarding of unreachable wounds | Offline |
| First aid with carried bandages for a reachable bleeding body region | Offline desktop path; no VR bandage action or mesh |
| Character studio: any mesh or object can become a character | Offline |
| Animation clips, Animation Lab editor, VR motion recording | Offline (VR recording path tested synthetically) |
| Full-detail GPU-skinned crowds and injured bodies | Offline render and performance reviews |

## Simulation

| Feature | State |
| --- | --- |
| Fixed-tick entity simulation with players, NPCs, items and rigid bodies | Offline; deterministic replay and scale tests |
| Range migration from the older home code into the shared simulation | Partial; desktop enables it by default, headset still uses the older path |
| Server-authoritative replication for VR and desktop player inputs | Synthetic packet-loss and local UDP loopback tests only |
| Live VR/desktop multiplayer between machines | Planned; no validated session |
| Secure multiplayer connection and proximity-based updates | Planned |
| Persistent contiguous world with shared construction | Planned |
| P9 pistol: slide, magazines, loose cartridges, pickup, recoil and ejected cases | Offline; some controller actions observed, current headset repeat open |
| M4-style carbine: 30-round magazines, safe/semi/auto selector and authored mounts | Offline; live VR handling open |
| P9 red-dot sight and flashlight with mount and light controls | Offline PC render and interaction tests |
| Material damage: bullet holes, shoot-through walls, breaking timber, ricochets, fragments | Offline |
| Player health: traced organ hits, fractures, bleeding, breathing, consciousness, grip, death | Offline |
| Injury rendering on CPU and GPU: entry/exit wounds, blood on skin and clothing, ragdolls | Offline |
| Car driving, seats, opening doors, tyre marks and crash deformation | Offline PC path |
| Crushed or punctured tyres and bent rims affect rolling | Offline |
| PC sound: engine, tyres, wind, footsteps, shots and handling | Offline playback and Sound Lab reviews; headset audio open |

See [Simulation and health](SIMULATION.md) for details.

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
| Asset Viewer | Browses people, worlds, weapons, accessories, clothing, props and vehicles from the content catalogs |
| Weapon Lab | Reviews authored weapons, grips and handling clips |
| Cloth Lab | Reviews garment layers and fit |
