# Test Report — RAAH Personal Edition 1.3

## Source / structural checks

- **PASS** — inline ES module extracted and accepted by `node --check`.
- **PASS** — HTML parsed using Python's HTML parser.
- **PASS** — no duplicate HTML IDs (111 unique IDs).
- **PASS** — all statically detected `$()` DOM ID references exist (99 references checked; no missing IDs).
- **PASS** — all six settlement IDs present (3 villages, 2 cities, 1 town).
- **PASS** — taxi overlay, destination travel function, door entry/exit functions, and interior room generation present.
- **PASS** — indoor named-NPC targeting metadata is present.
- **PASS** — save schema v11 plus v10 and earlier legacy keys present.
- **PASS** — taxi destination fallback handles both current coordinate property names.

## Intended-content checks

- **PASS** — 19 unique configured enterable building IDs found in source.
- **PASS** — six settlement taxi stands are created from the district-site array.
- **PASS** — source includes additional settlement population and named story-person definitions.
- **PASS** — existing Case 001, Case 002, Case 003, evidence journal, personal-story panel, map and save systems remain in source.

## Runtime tests

- **BLOCKED** — Headless Chromium attempted to load the HTML, but the external PlayCanvas CDN did not resolve/finish within the available execution time. The HTML document could not reach a stable rendered state in this environment.
- **NOT RUN** — manual Chrome/Edge interaction with mouse capture, moving around the full world, taxi trips and room portals.
- **NOT RUN** — end-to-end three-case campaign in a real browser.
- **NOT RUN** — actual GPU frame-time/FPS test on an integrated-graphics laptop.
- **NOT RUN** — detailed visual review of each city, village, interior and NPC animation from in-game screenshots.

## Honesty note

Static source validation cannot establish that a browser game will render or that each in-world object will be reachable. This is a significant scope expansion and needs a real Chrome/Edge test. The game uses an external PlayCanvas CDN, scripted NPCs, stylised procedural models, taxi fast travel, and portal-based interiors. It is not being represented as photorealistic or equivalent to a commercial AAA game's content volume.