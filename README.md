# MindARProject (WebAR)

Static WebAR demo built with A-Frame + MindAR Image Tracking. The experience is fully declarative in the `<a-scene>` within [index.html](index.html).

## Specs
- **Frameworks**: A-Frame 1.4.2, MindAR (image tracking) 1.2.2
- **Shaders**: aframe-vid-shader (video material)
- **Entry point**: [index.html](index.html)
- **Targets**: [StreamingAssets/targets.mind](StreamingAssets/targets.mind)

## Project structure
- [index.html](index.html) — A-Frame scene with MindAR image tracking
- [TrackableImages/](TrackableImages/) — images referenced in the scene
- [Modals/](Modals/) — glTF models (e.g., `flask.gltf`)
- [StreamingAssets/](StreamingAssets/) — MindAR `.mind` target bundles

## How it works
- `mindar-image` on `<a-scene>` loads the target bundle: `imageTargetSrc: \StreamingAssets\targets.mind;`
- Tracked content is anchored via `<a-entity mindar-image-target="targetIndex: 0">`
- Assets are declared in `<a-assets>` and referenced by id (e.g., `#my-video`, `#card`, `#avatarModel`)

## Running locally
This is a static site. Serve it from a local web server to allow camera permissions.

## Updating targets
Regenerate `targets.mind` and keep the path consistent with `imageTargetSrc` in [index.html](index.html).
