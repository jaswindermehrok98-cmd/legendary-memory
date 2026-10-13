# Changelog — RAAH Personal Edition 1.3

## District & story expansion

- Expanded the previous Sanjh setting into six linked settlements: one town, three villages, and two cities.
- Added connectors and an extended arterial road, local street networks, city side streets, field plots/furrows, street lights, trees, road borders and settlement signs.
- Added 6 static taxi ranks, 3 village tractors and city buses/auto-rickshaws (13 local vehicles including taxis).
- Added a taxi destination UI with fare quote, cash deduction, confirmation and fade transition. Taxi travel preserves case state and does not count as evidence.
- Added 19 marked enterable building portals with purpose-specific lightweight rooms and exit interactions.
- Added named people in interiors and a family/old-friend narrative track for Nav Bedi, including Baljit Kaur, Deep Sandhu and Mehak Gill.
- Added 15 named resident/side-character conversation profiles plus Iqbal, with source-aware, role-specific context that is not treated as physical evidence.
- Expanded pedestrian population with 19 local NPCs across the additional settlements and retained the earlier ambient pedestrians. NPC movement remains scripted and low-cost.
- Added settlement names and a large-scale schematic map that shares world coordinates with taxi destinations.
- Extended player movement boundaries and save validation for the wider world.
- Fixed taxi destination spawn coordinate normalization for Sanjh Town and ensured story NPC metadata is available to indoor targeting and relationship save state.

## Retained

- Previous Case 001–003 story, evidence and deduction systems.
- Existing PlayCanvas Engine architecture and first-person controller.
- Earlier source snapshots and documentation preserved in the ZIP.

## Known limitations

- Taxi service is fast travel at static taxi models, not a fully drivable vehicle simulation.
- Building interiors use portal/staging rooms, not a continuous, physically open building shell.
- Character models and most environment assets remain procedural/stylised; no new externally sourced character model is claimed.
- Scripted NPC routines are not advanced AI. Runtime rendering and exact laptop FPS are not verified in this build environment.