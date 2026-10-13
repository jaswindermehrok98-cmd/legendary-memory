# Test Report — RAAH Personal Edition 1.4

## Static checks
- **PASS** — JavaScript module passed `node --check`.
- **PASS** — HTML parsed.
- **PASS** — 111 unique HTML IDs; no duplicates.
- **PASS** — 99 static DOM references checked; no missing IDs.
- **PASS** — PlayCanvas 2.23.2 import retained.
- **PASS** — sky, filmic tone mapping, light/fog tuning, practical lights, road detail, and graphics presets are present in source.
- **PASS** — 1.3 baseline included in the package.
- **PASS** — ZIP integrity checked after packaging.

## Runtime checks
- **BLOCKED** — Headless Chromium attempt failed during graphics/EGL initialization in this environment, so no reliable live screenshot could be captured.
- **NOT RUN** — manual Chrome/Edge play session and visual comparison.
- **NOT RUN** — integrated-graphics frame-rate test.
- **NOT RUN** — full regression pass of district map, taxi, building portals, NPC interactions and all case progress after rendering changes.

## Interpretation
Static checks do not prove rendered appearance. The game still imports PlayCanvas from a CDN. Treat 1.4 as a rendering/art-direction upgrade awaiting real-device review, not as proof of AAA production quality.