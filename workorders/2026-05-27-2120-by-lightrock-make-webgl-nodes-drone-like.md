# Make WebGL demo nodes look like simple drones

## Purpose

Make the flying things in the public WebGL demo read visually as simple drones instead of colored spheres / wait-cursor-like nodes, without changing the demo's PFEM/PFCOMM architecture message.

The user explicitly does not want fancy imported 3D models. The goal is a light procedural visual improvement: simple objects that look more like drones while preserving the current demo behavior.

## Scope

Update the public GitHub Pages demo at:

```text
docs/webgl_demo3.html
```

Replace the current node visual shape with a simple procedural drone/quadcopter-like object using basic Three.js geometry. A good target shape is:

```text
central body
four short arms
four rotor rings/discs
same role-based colors
same movement and labels
same PFEM/PFCOMM link behavior
```

The drone objects should remain lightweight and generated entirely inside the single HTML file.

## Files/areas likely to change

```text
docs/webgl_demo3.html
```

Likely function areas:

```text
makeNodeMesh(...)
setNodeColor(...)
updateNode(...)
```

Possible nearby comments may be updated if needed to keep the file clear.

## Out of scope

Do not change:

```text
docs/index.html
README.md
examples/webgl-demo-3/README.md
workorders/README.md
schemas/workorder-contract.json
```

Do not add external model files, textures, GLTF/GLB assets, image assets, build tooling, npm packages, loaders, bundlers, or additional JavaScript files.

Do not redesign the PFEM/PFCOMM behavior, mission objective, ground target/airspace volume, event log, phase timing, labels, role meanings, or public page copy unless a tiny wording fix is strictly required by the node visual change.

Do not use image generation.

## Constraints

Keep the demo single-file and GitHub-Pages-friendly.

Use only procedural Three.js geometry already available from the imported Three.js module.

Preserve the architecture demonstration:

```text
PFEM and PFCOMM remain distinct overlays.
Every node can be both a PFEM participant and a PFCOMM participant.
Roles remain declared/negotiated scenario roles, not fixed species.
Active, degraded, lost, protected, latent, and replacement states remain visually distinct.
```

Keep role color coding intact. The new drone geometry must be recolored by the existing role/state color changes. If `makeNodeMesh()` returns a `THREE.Group`, update `setNodeColor()` safely so all color-bearing child meshes update.

Keep labels, rings, motion, mission lines, pair lines, HUD metrics, legend, and controls working.

The drones do not need to be fancy. They should be readable at demo scale: body plus arms plus rotors is enough.

## Required checks

Perform at least these checks:

```text
manual review of docs/webgl_demo3.html diff
confirm docs/webgl_demo3.html still contains exactly one HTML document
confirm the Three.js import remains unchanged or explain why not
confirm no new files were added
open / inspect the public demo locally or through GitHub Pages if available
browser console smoke check for JavaScript syntax/runtime errors if a browser is available
```

If a browser is not available, state that clearly in the completion note and do a careful static JavaScript review around the changed functions.

## Expected result

The public WebGL demo still works at:

```text
https://lightrock.github.io/drbones/webgl_demo3.html
```

The moving nodes now look like simple drone/quadcopter-like flying objects instead of colored spheres.

Role/state colors still change correctly. Degraded/lost states remain legible. PFEM/PFCOMM lines still attach to the moving drone objects. The rectangular ground target and airspace volume remain as-is.

## Fallback behavior

If changing `makeNodeMesh()` to return a `THREE.Group` causes unsafe breakage, stop and report the exact blocker rather than rewriting the demo broadly.

A valid fallback is to keep each node as a single `THREE.Group` with simple body/arm/rotor child meshes and adjust only `setNodeColor()` and any direct material assumptions needed for that group.

If the demo cannot be tested in a browser, do not claim browser validation. Report the static checks performed and the untested browser risk.

## Completion note

The executor must report:

```text
changed files
checks run
checks passed or failed
checks not run and why
lessons learned created or not needed
open questions
exact workorder path
```

Use this exact workorder path in the completion note:

```text
workorders/2026-05-27-2120-by-lightrock-make-webgl-nodes-drone-like.md
```
