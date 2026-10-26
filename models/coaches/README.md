# iFocus Fitness coach models (Meshy, rigged, web-optimised)

Asset branch only. Not for deploy. GitHub Pages builds from `main`, so nothing here is live.

| Coach | File | Film still | Joints | Clips |
| --- | --- | --- | --- | --- |
| Avery (male_A) | avery.glb | previews/male_A.jpg | 50 | Running, Walking |
| Ellis (male_B) | ellis.glb | previews/male_B.jpg | 44 | Running, Walking |
| Maren (female_A) | maren.glb | previews/female_A.jpg | 70 | Running, Walking |
| Ione (female_B) | ione.glb | previews/female_B.jpg | 32 | Running, Walking |

- Skeleton: Mixamo naming (`mixamorig:Hips`, `Spine`, `Spine1`, `Spine2`, `Neck`, `Head`, `LeftArm`, `LeftForeArm`, `LeftHand`, `LeftUpLeg`, `LeftLeg`, `LeftFoot`, etc.), one SkinnedMesh per file, 1.7 m tall, feet at y=0, bind pose is an A-pose.
- Compression: EXT_meshopt_compression + KHR_mesh_quantization, textures EXT_texture_webp at 2048. Load with GLTFLoader + `setMeshoptDecoder(MeshoptDecoder)` from `three/examples/jsm/libs/meshopt_decoder.module.js`.
- Clips: only Meshy's Running and Walking. No idle clip, so idle breathing and exercise motion must be procedural on the bones.
- Glow: Avery and Maren have the cyan visor in the texture. Ellis's headband and arm glow are missing from the texture and Ione's headband is faint; add emissive geometry/material in code (parent to `mixamorig:Head`, arm bones).
