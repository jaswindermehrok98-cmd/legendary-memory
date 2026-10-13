# RAAH: The Unmarked Route

A personal, single-player first-person investigative browser game set in fictional contemporary Punjab.

## Current build

**RAAH Personal Edition 1.4 — Cinematic Visual Pass**

- `index.html` is the playable entry point.
- `game/raah_personal_edition_1.4.html` is the versioned source.
- `baselines/raah_personal_edition_1.3.html` preserves the prior baseline.

## World and gameplay

The current district includes Sanjh Town, Nawanagar City, Fatehgarh City, Chakk Dhaliwal, Bhagatpura, and Kalanpur. Systems include taxi fast travel, portal-based enterable building scenes, Nav Bedi's personal story, optional character conversations, three connected investigations, an evidence journal, hypothesis testing, and local save data.

## Visual work in 1.4

The visual pass adds a procedural late-monsoon sky dome, filmic tone mapping and sRGB output when supported by PlayCanvas, tuned lighting and atmospheric fog, improved shadow casting for major building volumes, three practical lights, additional road markings, a cinematic grade layer, antialiasing, and refined graphics presets.

## Run locally

Use a modern desktop browser (Chrome or Edge recommended) with JavaScript and WebGL enabled. The game loads PlayCanvas Engine 2.23.2 from jsDelivr, so internet access is needed.

From the repository root:

```bash
python -m http.server 8000
```

Open `http://localhost:8000`, press **Begin fieldwork**, and click the game view to capture the mouse.

## Controls

- **WASD** — move
- **Mouse** — look
- **Shift** — run
- **E** — interact / inspect / talk / enter / taxi
- **J** — journal
- **M** — district map
- **P / Escape** — pause or release pointer, depending on context

## Documentation

- [1.4 README](docs/README_RAAH_Personal_Edition_1.4.md)
- [Changelog](docs/CHANGELOG_RAAH_1.4.md)
- [Test report](docs/TEST_REPORT_RAAH_1.4.md)
- [Asset manifest](docs/ASSET_MANIFEST_RAAH_1.4.md)
- [Full-game overhaul prompt](docs/RAAH_Claude_Full_Game_Overhaul_From_1.3.md)

## Limitations

RAAH is a stylised procedural browser-game prototype, not a photorealistic AAA production. Character rigs and much of the environment remain procedural; NPC routines are scripted; taxi is fast travel; and interiors use portal transitions rather than seamless spaces. The visual upgrade requires manual browser review and laptop performance testing.