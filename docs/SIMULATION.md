# Simulation and health

The PC simulates the world, and the renderer and the stream show the result. The systems below have offline tests and reviews, but this page does not claim a completed live headset or multiplayer session.

## Shared simulation and multiplayer

The new fixed-tick simulation has an entity component system for players, NPCs, loose items and physical bodies. It connects existing health, firearm, animation, damage and vehicle systems to one game state. VR and desktop players use the same simulated entity kind; only their input source differs. The desktop console runs the new path by default, while the native Quest Link session still runs the older home path. The range cutover is incomplete, with some state shared between both implementations.

The game network is server-authoritative: clients send input, and the server sends bounded state updates and shot, hit and injury events. Remote entities are interpolated. Synthetic tests cover loss, reordering, duplicates and late joins; UDP has been tested on local loopback. These tests do not establish a live multi-PC or headset multiplayer session. The current endpoint trusts a LAN; it lacks a secure connection handshake, encryption and interest management. Damage geometry and persistent world edits are not yet replicated. The game network is independent of the Quest Link USB video and tracking link.

## Player health

Each posed player and range figure has its own health model:

- **Hits are traced, not rolled.** A projectile's path through the body decides which region and which internal organs it reaches, and whether it exits.
- **Consequences follow from injuries.** Fractures, bleeding rate, breathing, consciousness, movement, weapon grip and death are derived from the organs and regions that were hit.
- **Shared rendering.** Entry and exit wounds, blood on skin and clothing, and blood in the world all come from one injury state, on both the CPU and the GPU renderer.
- **Reactions.** Faces flinch, show pain and look at the wound. A standing figure presses on wounds it can reach and guards one it cannot. Unconscious and dead bodies become ragdolls with limb contact.
- **Clothing.** Each worn garment records entry and exit marks, blood and wetness (rain or water) separately.
- **Desktop HUD.** A health page shows a front/back hit map, the organs struck and the hit counts.
- **First aid.** A desktop player starts with two carried bandages, can pick up more and can wrap a reachable bleeding region. The wrap stops that region's bleeding; it does not heal unrelated wounds. VR use and a visible bandage mesh are still open.

This is a game model. It is not a medical or wound-ballistics model.

## Firearms and material damage

- **Data-driven firearms.** The P9 pistol has a slide, a magazine and loose cartridges that can be loaded one by one. Accessories (flashlight, red dot sight) mount to it. An M4-style carbine has 30-round magazines and a safe/semi/auto selector. PC handling is tested offline; current VR handling needs a live repeat.
- **Training house.** Six furnished rooms across two storeys deal hostage holds and armed-suspect scenarios in varied order. Backup gunmen can return fire around cover, reload, flinch when hit and drop their pistols. The run tracks room clears, errors and a saved result.
- **Materials decide the outcome.** Every shootable object declares a material. Bullets leave holes, lead splashes, craters or paint scrapes depending on what they hit.
- **Shoot-through panels.** Thin walls, booth dividers and roofs erode from both faces into ragged holes that later bullets pass through. Penetration stops at a finite depth (for example, a 9 mm round through about 0.3 m of pine).
- **Fracture.** Timber members break after a group of hits and drop whatever they were holding.
- **Ricochets and fragments.** Grazing bullets ricochet by material, flatter and slower, with an audible whine. Bullets can break up into fragments that wound.
- **Debug view.** The desktop console can draw every bullet trace as a line.

## Vehicles

- **Rigid-body car.** The race car can be driven with tracked hands or the keyboard. It has opening doors and seats for passengers.
- **Crash deformation.** An elastoplastic deformation lattice gives crumple zones that absorb the impact energy. Every drawn part keeps its dent.
- **Wheels and tyres.** Tyres can be crushed or punctured and rims can bend. A damaged tyre shakes the suspension and loses grip.
- **Tyre marks.** Sliding tyres lay rubber, scuff and earth marks on the ground.
- **Shared-sim migration.** The new simulation also models car collisions with walls, people and other cars, with seats and door anchors read from the vehicle model. These slices are offline and are still being connected to the full game path.

## Water, weather and nature

- **Surf.** A nonlinear shallow-water simulation shoals swell into breaking bores that flood and drain the beach, leaving foam, spray and drying wet sand.
- **Underwater.** Reefs with seagrass, rigid corals, kelp that bends around bodies, and fish that flee. Players can swim and dive.
- **Weather.** Three cloud layers, a storm and clearing cycle, cloud shadows, depth-tested rain and wet ground.
- **Foliage contact.** Palm fronds, each individual leaflet, plants and grass respond to heads, hands and fingertips at measured contact sizes.

## Sound

Engine, tyre, wind, footstep and firearm sounds play on the PC. Sound Lab catalogs and reviews the designs; some shot and handling sounds are resynthesized from measured recordings. Headset audio is not implemented yet.
