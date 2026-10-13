# RAAH Personal Edition 1.4 — Cinematic Visual Pass

This release continues from Personal Edition 1.3 and focuses on rendering, lighting, surface response, road details, and cinematic atmosphere while preserving the six-settlement district and existing story systems.

## Run
Use a current desktop version of Chrome or Edge with JavaScript and WebGL enabled. The PlayCanvas Engine is loaded from jsDelivr, so internet access is required.

From the package directory, run:

```bash
python -m http.server 8000
```

Open `http://localhost:8000` and press **Begin fieldwork**. Click the game view to capture the mouse.

## Controls
- **WASD** — move
- **Mouse** — look
- **Shift** — run
- **E** — interact / inspect / talk / enter / taxi
- **J** — journal
- **M** — map
- **P / Escape** — pause or release pointer depending on context

## Visual changes in 1.4
- Added a deterministic, procedural late-monsoon sky dome with a vertical gradient, soft cloud banks, and warm low-horizon glow; no external image files are required.
- Enabled sRGB output and filmic tone mapping through the camera when supported by the loaded engine.
- Tuned directional daylight and atmospheric fog for stronger mid-distance separation.
- Increased main directional shadow resolution and enabled shadow casting on district building volumes and selected character bodies.
- Added low-range practical lights at story-relevant evening locations.
- Added lane dashes, subtle asphalt repair patches, and stylised crosswalks at city intersections.
- Updated rendering presets to Performance 0.60, Balanced 0.78, and Sharper 1.0; antialiasing is requested at device creation.
- Added a restrained cinematic color-grade layer while keeping the interactive UI above it.

## Important limitations
This remains a stylised procedural browser game, not a commercial AAA production. The art direction and rendering pipeline are improved, but bespoke character rigs, hand-authored high-detail environment assets, advanced reflections, ambient occlusion, extensive animation, and full sound production are not included. Runtime visuals and integrated-GPU performance need testing on the intended laptop.

The 1.3 source is retained in `baselines/` for direct comparison.