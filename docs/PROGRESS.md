# Progress log

The project started on 2026-09-26. The main repository has about 150 commits as of 2026-10-04.

## 2026-09-26: First image in the headset

- Built the independent stereo pipeline and cable PCVR groundwork.
- Native USB Link: the host completed the session handshake and started the stock Link runtime. HEVC video from the PC appeared in the stock receiver.
- Head, controller and optical-hand tracking reach the PC home.
- Added session recovery groundwork and diagnostics bundles.

## 2026-09-27: The PC world and the desktop

- Added a PC render view, a mirror and a world editor that share one live world with the headset.
- Desktop players can join the live world with IK-animated bodies.
- Added character authoring: any source mesh can become a character.
- Added a textured world asset pipeline, and improved avatar detail and VR frame pacing.

## 2026-09-28: Island and engine structure

- Added avatar body contact, head-turn IK and desktop player physics.
- Palms, grass and plants react to touch.
- Added weather: rain, cloud layers and cloud shadows (also GPU-drawn in the desktop editor).
- Split the code into a layered crate workspace with an automated layer check.

## 2026-09-29: Engine core and GPU path

- Added an engine frame loop. Built-in worlds, terrain and materials became editable data.
- Islands are generated from a seed and a few settings.
- Opt-in Vulkan renderer and in-process HEVC encoder for the headset frame.
- Added an underwater world with swimming, and arm-driven VR locomotion.

## 2026-10-02: Race circuit

- Added a drivable race car with rigid-body dynamics and hand-tracked controls, plus desktop driving.

## 2026-10-03: Range, damage and health

- Added a shooting range, a data-driven firearm simulation and vehicle crash deformation.
- Sound Lab: procedural engine and pistol sounds, catalogued and reviewable.
- Player health with wounds, injury rendering and GPU-skinned bodies.
- Sun shadows from all world props and vehicles.

## 2026-10-04: Animation, clothing and materials

- Animation system: clips, Animation Lab and a VR movement recording path.
- Clothing and equipment system with wet and damage appearance.
- Four-room training course, pistol accessories (flashlight, red dot).
- Material panels: shoot-through walls, ricochets, bullet fragments and debug traces.
