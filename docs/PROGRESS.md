# Progress log

The project started on 2026-09-26. Newest entries are at the top. Offline, synthetic and headset results are distinguished below.

## 2026-11-28 — PC render gallery

The gallery now includes the stalls and east watch at Market Crossroads. The Biomes trail views show the updated foliage lighting and ground textures. The aircraft views show the helicopter’s four-blade rotor, the fighter’s revised wing panels and the Cessna’s blue livery. [View the gallery](../README.md#gallery)

## 2026-11-23 — Arena, Biomes and No Man's Land

- **Arena.** NPCs can duel and fight in teams. The PC simulation handles sword and shield contact, armour, unarmed strikes and archery, including individual arrows in the quiver.
- **Biomes.** Ten starting points cover the meadow, woods, heath, river and lake. The world adds a worn trail, forest-floor materials, distance haze, and rain with puddles and drop rings.
- **No Man's Land.** Two NPC infantry teams fight across trench networks and capture points. Mortar impacts throw dirt and leave craters in the simulated terrain. Optional harassing fire produces impacts during exploration.
- **PC gallery.** New renders show a longsword duel between NPCs, four views of Biomes, and three stages of the same mortar impact. [View the gallery](../README.md#gallery)

## 2026-11-15: Aircraft damage, crew gear, NPC tactics and benches

All items below are offline PC and desktop results. None has been checked in the headset yet.

- **Aircraft structure and damage.** The fighter, the Cessna-class plane, the helicopter and the hatchback now have an internal structure with systems. Hits pass through it layer by layer and leave entry and exit holes, dents and streaks. Flight and crash loads, overload, fatigue, internal fires and explosions can break parts away, with fragments and jagged edges. Fixed benches measure overload, crash break-up and explosions.
- **Flight models measured from the 3D models.** Each aircraft's lift, drag and roll now come from its drawn shape, checked in the wind tunnel and on the flight bench. Every bench run is inside its expected ranges.
- **Fighter and cockpits.** Smoother fighter model with gear bays, smaller canards, armament stations and loadouts, an HSD navigation page, a clickable oxygen connector and outer-wing airbrakes. The helicopter got clickable engine switches, a height-holding hover mode and position hold. Pilots' hands now rest on the stick, throttle, cyclic and collective.
- **Crew gear and physiology.** Flight suit, helmet with a hinged visor and an oxygen mask; a modular helicopter helmet with night-vision goggles, face shield and battery. Altitude hypoxia and g-force blackout build up with tunnel vision and grey-out.
- **Rockets and ballistics.** 6-DOF unguided rockets for the helicopter, ground vehicles and jet pods, a ballistics simulator for bullets, shells and bombs, and mounted rotary guns. Each has its own scenario bench.
- **NPC awareness and tactics (opt-in).** NPCs can see, hear, raise their alert level, lose morale and pick cover. Squad commands, scripted civilians and a learned squad leader trained by reinforcement learning were added and judged on a tactics bench.
- **World and weather.** A moonlit night with airfield ground lights, a longer view distance from aircraft, time of day in the weather panel, and rain on the simulated ground that follows the visible weather. Placed cars, aircraft, people and weapons now work in any world through the one shared simulation.
- **Players and weapons.** Re-modelled pistol and carbine, shouldered carbine with a cheek weld and prone hold, worn garments that can be taken off and put on, smoother walking, and stamina that recovers while seated and drains while swimming fast.
- **Preview gallery.** Vehicles, outfits and worlds re-rendered on the GPU with the real world, fabric and avatar textures.
- **Performance.** A live-play bench drives the whole desktop console with a bot. Weapons and the player's own body are drawn as GPU instances, and shadows are computed on a worker thread.

## 2026-10-19: Aircraft, weather and sound

- First aircraft simulation: a Cessna-class plane, a delta-canard twin-jet fighter and a utility helicopter fly in an airfield world with a clickable cockpit, instrument displays, gear, brakes and crash consequences. Offline and desktop only; no headset check yet.
- A virtual wind tunnel and fixed flight and crash scenario benches measure every aircraft in every weather and flight phase, so handling changes are compared against a baseline.
- Dynamic weather from clear sky to thunderstorm, with rain on glazing, wing vapour and first rain, wind and thunder sounds. Sound design is the next open area.
- Aircraft sun shadows follow the model's shape.

## 2026-10-11: Shoothouse run and weather video

- A cut shoothouse run shows reworked movement, NPCs, a fear system and stamina. Weather with sound and the FLUID wave system were shown in short videos.

## 2026-10-09: Shared simulation cutover and multiplayer groundwork

- Added a fixed-tick entity simulation with rigid-body physics and shared player, NPC and item state. Damage, health, firearms, animation, vehicles and training-course rules are moving from the older home code into it.
- The desktop console enables the simulation bridge by default. The native Quest Link session still leaves it disabled; the full cutover and headset review are open.
- Server-authoritative game replication for VR and desktop inputs passes synthetic packet-loss tests and local UDP loopback. There is no validated live multiplayer session or public-network security yet.
- Car collision, seat and door data, held weapons and wound rendering gained offline simulation-side slices. A persistent contiguous world remains a plan.

## 2026-10-04: Animation, clothing and materials

- Animation system: clips, Animation Lab and a VR movement recording path.
- Clothing and equipment system with wet and damage appearance.
- Four-room training course, pistol accessories (flashlight, red dot).
- Material panels: shoot-through walls, ricochets, bullet fragments and debug traces.

## 2026-10-03: Range, damage and health

- Added a shooting range, a data-driven firearm simulation and vehicle crash deformation.
- Sound Lab: procedural engine and pistol sounds, catalogued and reviewable.
- Player health with wounds, injury rendering and GPU-skinned bodies.
- Sun shadows from all world props and vehicles.

## 2026-10-02: Race circuit

- Added a drivable race car with rigid-body dynamics and hand-tracked controls, plus desktop driving.

## 2026-09-29: Engine core and GPU path

- Added an engine frame loop. Built-in worlds, terrain and materials became editable data.
- Islands are generated from a seed and a few settings.
- Opt-in Vulkan renderer and in-process HEVC encoder for the headset frame.
- Added an underwater world with swimming, and arm-driven VR locomotion.

## 2026-09-28: Island and engine structure

- Added avatar body contact, head-turn IK and desktop player physics.
- Palms, grass and plants react to touch.
- Added weather: rain, cloud layers and cloud shadows (also GPU-drawn in the desktop editor).
- Split the code into a layered crate workspace with an automated layer check.

## 2026-09-27: The PC world and the desktop

- Added a PC render view, a mirror and a world editor that share one live world with the headset.
- Desktop players can join the live world with IK-animated bodies.
- Added character authoring: any source mesh can become a character.
- Added a textured world asset pipeline, and improved avatar detail and VR frame pacing.

## 2026-09-26: First image in the headset

- Built the independent stereo pipeline and cable PCVR groundwork.
- Native USB Link: the host completed the session handshake and started the stock Link runtime. HEVC video from the PC appeared in the stock receiver.
- Head, controller and optical-hand tracking reach the PC home.
- Added session recovery groundwork and diagnostics bundles.
