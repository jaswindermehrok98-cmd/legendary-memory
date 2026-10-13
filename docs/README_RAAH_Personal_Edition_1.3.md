# RAAH Personal Edition 1.3 — Sanjh District Expansion

## What this build adds

- Six linked settlements: **Sanjh Town**, villages **Chakk Dhaliwal**, **Bhagatpura**, **Kalanpur**, and cities **Nawanagar City** and **Fatehgarh City**.
- An expanded connected terrain and road spine with settlement connectors, town/city streets, rural fields, local signs, utility details, and a schematic district map.
- Six taxi ranks and a taxi destination service. Press **E** while looking at a taxi to select a settlement, review the rupee fare, confirm the trip, and arrive after a short screen fade. This is an inexpensive fast-travel system; vehicles are **not yet player-drivable**.
- Nineteen enterable building portals leading to small, furnished rooms (homes, workshops, clinics, offices, shops/cafés and records spaces). Press **E** while looking at a marked door, explore the room, speak to its named occupant where present, and look toward the entry door to exit. These rooms are portal/staging interiors, not yet seamlessly connected shell interiors.
- A larger pedestrian and character layer, including role-specific neighbourhood context and named side characters: Baljit Kaur (Nav's mother), Gurdeep “Deep” Sandhu (childhood friend), Mehak Gill (reporter), Iqbal Singh (taxi driver), and residents/workers at the clinics, records offices, workshops, co-op and villages.
- A personal-story card that updates as Nav talks to significant characters. Conversations remain separate from physical evidence and do not auto-solve the cases.
- Save schema v11 supports the six settlement destinations, wallet, visited locations, story relationship flags, and current interior state, while keeping v10 and earlier key migration.

## Launch

1. Extract the ZIP.
2. Keep an internet connection available because PlayCanvas Engine 2.23.2 is imported from jsDelivr.
3. Open `raah_personal_edition_1.3.html` in current Chrome or Edge. If opening a local file is blocked by browser policy, open a terminal in the extracted folder and run `python -m http.server 8000`, then visit `http://localhost:8000/raah_personal_edition_1.3.html`.
4. Click **Begin fieldwork**, then click the game view once to capture mouse look.

## Controls

- **WASD**: move
- **Mouse**: look
- **Shift**: run
- **E**: inspect evidence, talk, enter/leave an interior, or use a taxi rank
- **J**: journal
- **M**: district map
- **P / Escape**: pause/menu (context-sensitive)

## Notes

- Taxi fares are deducted from Nav's in-game wallet. Walking remains possible everywhere.
- Taxi travel moves the player to a named settlement spawn; it does not skip case prerequisites or record evidence.
- Doors use explicit interaction/portal transitions. Building contents are placed in a separate low-cost interior area to avoid rendering every interior at once.
- NPC routines are scripted state machines/waypoints, not generative AI. Some interactions are optional context, not case evidence.
- Important graphics are intentionally stylised/procedural. This version prioritises a larger functional district over photorealism.
- Browser runtime rendering, complete story playthrough, exact FPS, and all NPC routes still need in-browser verification on the target laptop. See the test report.

## Save and compatibility

The new primary key is `raah-unmarked-route-save-v11`. Older keys are retained as migration inputs and are not removed merely by loading the game. Export a save from the pause menu before experimenting with resets or manually edited saves.