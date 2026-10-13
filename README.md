# RAAH: The Unmarked Route

A personal, single-player first-person investigative browser game set in the fictional contemporary Punjabi district of Sanjh.

## Current build

**RAAH Personal Edition 1.3 — District Expansion**

The playable entry point is [index.html](./index.html). The game source is stored as a compressed, lossless HTML asset in `game/`; the launcher decompresses it in modern desktop browsers and runs it in an iframe.

## World and gameplay

- Six connected settlements: Sanjh Town, Nawanagar City, Fatehgarh City, Chakk Dhaliwal, Bhagatpura, and Kalanpur.
- Taxi fast travel, with in-game fares.
- Portal-based enterable buildings and furnished interior scenes.
- Nav Bedi's personal story and named side characters.
- Three connected investigations, evidence journal, witness testimony, hypotheses, and local save data.
- First-person keyboard/mouse controls.

## Run locally

A modern desktop browser with WebGL 2, JavaScript enabled, and internet access for the PlayCanvas Engine CDN is required.

Recommended:
1. Download or clone this repository.
2. Run `python -m http.server 8000` from the repository root.
3. Open `http://localhost:8000/` in Chrome or Edge.
4. Click **Begin fieldwork** and click the game view to enable mouse look.

The compressed source can be recovered with `gzip -dc game/raah_personal_edition_1.3.html.gz > raah_personal_edition_1.3.html`.

## Controls

- **WASD** move
- **Mouse** look
- **Shift** run
- **E** inspect, talk, enter/leave a building, or use a taxi
- **J** journal
- **M** district map
- **P / Escape** pause/menu (context-sensitive)

## Documentation

- [Version 1.3 changelog](./docs/CHANGELOG_RAAH_1.3.md)
- [Test report](./docs/TEST_REPORT_RAAH_1.3.md)
- [Asset manifest](./docs/ASSET_MANIFEST_RAAH_1.3.md)
- [Master full-game overhaul prompt](./docs/RAAH_Claude_Full_Game_Overhaul_From_1.3.md)

## Important limitations

This is a stylised procedural browser-game prototype, not a photorealistic AAA production. NPC routines are scripted, vehicles are not player-drivable, and building interiors use portal transitions rather than seamless interiors. The prior test report records which checks passed and which runtime/gameplay checks remain unverified. The project should be tested in a real desktop browser before treating the whole campaign as verified.

## Project history

Earlier baselines are retained in Git history through the development work; the 1.3 package itself also includes the 0.7, 1.1, and 1.2 baseline HTML files.
