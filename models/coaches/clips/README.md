# Coach animation clips (asset branch, not for deploy)

Animation-only GLBs: skeleton nodes plus one animation each. No mesh, skin, materials or textures.
Source: Meshy preset animations exported on each coach's own rig (Mixamo skeleton), so clips are per coach.

Layout: `models/coaches/clips/<coach>/<Name>.glb`, coach = avery | ellis | ione | maren.

| Name | Meshy preset | Duration (s) |
| --- | --- | --- |
| Idle | Idle_02 | 1.87 |
| Press | Sumo_High_Pull | 2.57 |
| Curl | bicep_curl | 5.87 |
| Squat | air_squat | 1.87 |
| Pushup | push_up | 1.50 |
| JumpingJacks | jumping_jacks | 1.10 |
| Talk | Talk_Passionately | 10.27 |

Each file has one animation named as above, with rotation and translation tracks on every joint.
After GLTFLoader name sanitising, track targets (e.g. `mixamorigLeftHand`) match the nodes in `models/coaches/<coach>.glb` exactly (checked with three.js r169: 0 unbound tracks).

Processing: gltf-transform resample (tolerance 1e-4), dedup, prune, EXT_meshopt_compression (filter mode, quantised).
Load with GLTFLoader + `setMeshoptDecoder(MeshoptDecoder)`, then `mixer.clipAction(gltf.animations[0])` on the coach's scene.

Known issue: in Push up the Hips translation is baked roughly 1.5 to 2 m below the floor (source data, hips Y from -2.0 to -1.1 on Avery).
The player needs a vertical offset for this clip (or strip Hips Y translation and place the body on the floor in code).
Running and Walking are already in the coach model files. Maren's stray 360 spin jump is not exported.
