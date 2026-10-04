# Health and simulation

The PC simulates the world, and the renderer and the stream only show the result. Every system below is deterministic and covered by automated offline tests. None of them has been reviewed in the headset yet.

## Player health

Each posed player and range figure has its own health model:

- **Hits are traced, not rolled.** A projectile's path through the body decides which region and which internal organs it reaches, and whether it exits.
- **Consequences follow from injuries.** Fractures, bleeding rate, breathing, consciousness, movement, weapon grip and death are derived from the organs and regions that were hit.
- **Shared rendering.** Entry and exit wounds, blood on skin and clothing, and blood in the world all come from one injury state, on both the CPU and the GPU renderer.
- **Reactions.** Faces flinch, show pain and look at the wound. A standing figure presses on wounds it can reach and guards one it cannot. Unconscious and dead bodies become ragdolls with limb contact.
- **Clothing.** Each worn garment records entry and exit marks, blood and wetness (rain or water) separately.
- **Desktop HUD.** A health page shows a front/back hit map, the organs struck and the hit counts.

This is a game model. It is not a medical or wound-ballistics model.

## Firearms and material damage

- **Data-driven firearms.** The pistol has a slide, a magazine and loose cartridges that can be loaded one by one. Accessories (flashlight, red dot sight) mount to it. It works with VR hands and desktop controls.
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

## Water, weather and nature

- **Surf.** A nonlinear shallow-water simulation shoals swell into breaking bores that flood and drain the beach, leaving foam, spray and drying wet sand.
- **Underwater.** Reefs with seagrass, rigid corals, kelp that bends around bodies, and fish that flee. Players can swim and dive.
- **Weather.** Three cloud layers, a storm and clearing cycle, cloud shadows, depth-tested rain and wet ground.
- **Foliage contact.** Palm fronds, each individual leaflet, plants and grass respond to heads, hands and fingertips at measured contact sizes.

## Sound

Engine, tyre, wind and pistol sounds are generated procedurally from physical modes of the struck parts. Every sound is catalogued and reviewed in Sound Lab. For now, sound plays on the desktop only, because headset audio is not implemented yet.
