# Copilot instructions for MindARProject

## Project overview
- This is a static WebAR demo built with A-Frame + MindAR Image Tracking; the entry point is [index.html](index.html).
- All functionality is declarative in the `<a-scene>` tree (no separate JS files).
- External dependencies are loaded via CDN scripts:
  - A-Frame 1.4.2
  - MindAR (image tracking) 1.2.2
  - A-Frame video shader (aframe-vid-shader)

## Key structure and data flow
- The scene uses `mindar-image` with `imageTargetSrc` pointing to [StreamingAssets/targets.mind](StreamingAssets/targets.mind). Updating the target set requires regenerating this file and keeping the path consistent.
- Tracked content is anchored via `<a-entity mindar-image-target="targetIndex: 0">` in [index.html](index.html). Add new targets by adding more entities with incremented `targetIndex`.
- Assets are declared inside `<a-assets>` and referenced by id elsewhere (e.g., `#my-video`, `#card`, `#avatarModel`). Keep this pattern when adding images, videos, or 3D models.
- Project assets live in:
  - [TrackableImages/](TrackableImages/) for images used or referenced in the scene
  - [Modals/](Modals/) for glTF models (e.g., `flask.gltf`)
  - [StreamingAssets/](StreamingAssets/) for MindAR `.mind` target bundles

## Conventions and examples
- Use A-Frame primitives and components directly in HTML (e.g., `<a-plane material="shader: flat; src: #my-video">`). See [index.html](index.html) for the existing pattern.
- Keep asset references consistent with the current absolute paths used in HTML (e.g., `/TrackableImages/...`, `/Modals/...`).
- Animation is done via A-Frame component attributes on entities (example: `animation="property: position; ..."` on the glTF model).

## Workflows
- No build tooling or tests are present. Changes are made directly in [index.html](index.html) and static assets.
- Runtime relies on browser camera permissions; run from a local web server when testing AR features.
