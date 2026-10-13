# RAAH: The Unmarked Route

A personal, single-player first-person investigative browser game set in a fictional contemporary Punjabi district.

## Current build

**RAAH Personal Edition 1.3 — District Expansion**

- `index.html` is the playable entry point.
- `game/raah_personal_edition_1.3.html` is the versioned source copy.
- Game systems and much of the world are procedural and stylised.

## World and gameplay

The current design includes six settlements: Sanjh Town, Nawanagar City, Fatehgarh City, Chakk Dhaliwal, Bhagatpura, and Kalanpur. Gameplay systems include taxi fast travel, portal-based enterable building scenes, Nav Bedi's personal story, optional characters, three connected investigations, evidence and witness journals, hypothesis testing, and local browser saves.

## Run locally

Use a modern desktop browser (Chrome or Edge recommended) with JavaScript and WebGL 2 enabled. The game loads PlayCanvas Engine from jsDelivr, so an internet connection is needed to start it.

For a local server, run this command from the repository root:

```bash
python -m http.server 8000
```

Then open [http://localhost:8000](http://localhost:8000).

Opening directly through `file://` may not work reliably due to browser restrictions.

## Controls

- **WASD** — move
- **Mouse** — look
- **Shift** — run
- **E** — interact, inspect, talk, enter/leave, or use taxi
- **J** — journal
- **M** — district map
- **P / Escape** — pause or release the pointer, depending on context

## Documentation

- [Version 1.3 README](docs/README_RAAH_Personal_Edition_1.3.md)
- [Changelog](docs/CHANGELOG_RAAH_1.3.md)
- [Test report](docs/TEST_REPORT_RAAH_1.3.md)
- [Asset manifest](docs/ASSET_MANIFEST_RAAH_1.3.md)
- [Master overhaul prompt](docs/RAAH_Claude_Full_Game_Overhaul_From_1.3.md)

## Known limits

This is a stylised procedural browser-game prototype, not a photorealistic AAA production. NPC routines are scripted, vehicles are not player-drivable, and enterable buildings use portal transitions rather than seamless continuous interiors. Read the test report before assuming the full campaign or browser performance has been verified.
