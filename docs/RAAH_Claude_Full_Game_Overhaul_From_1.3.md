# RAAH: The Unmarked Route — Full-Game Overhaul & Completion Prompt
## For Claude Sonnet 5.5 Max — Use the latest RAAH 1.3 project as the baseline

You are the complete development team for my personal game project: game director, technical director, browser-game engineer, gameplay designer, narrative designer, level/world designer, environment artist, character artist, animation/AI programmer, UI/UX designer, audio designer, QA engineer, and release engineer.

**This is one integrated, whole-game task. Do not focus only on one feature or one subsystem.** I want you to take the latest project, audit the entire game, and improve the world, story, characters, NPCs, buildings, travel, missions, investigations, UI, saving, audio, performance, and reliability as one coherent product. Implement in the actual files and return a runnable build. Do not merely give advice or another plan.

The objective is a substantial, enjoyable personal browser game. It does not need to pretend to be photorealistic or claim to be equivalent to a commercial AAA production. If high realism is not achievable with the available assets, choose a coherent, polished, intentional stylised 3D art direction instead. **A consistent stylised game with functional systems is better than an allegedly realistic game made of primitive shapes and broken features.**

---

# 0. BASELINE LOCK — NON-NEGOTIABLE

Use **RAAH Personal Edition 1.3** as the primary baseline. Files may be named:

- `raah_personal_edition_1.3.html`
- `RAAH_Personal_Edition_1.3.zip`
- `README_RAAH_Personal_Edition_1.3.md`
- `CHANGELOG_RAAH_1.3.md`
- `TEST_REPORT_RAAH_1.3.md`
- `ASSET_MANIFEST_RAAH_1.3.md`

Use the supplied 1.3 files as the source of truth. The 1.1, 1.2, 0.8, and 0.7 versions may be useful for recovering an existing feature, but **do not revert to 0.7 or replace 1.3 with an unrelated project**. Preserve an untouched backup. If the latest 1.3 files are missing, stop and request the specific missing file; do not pretend that you inspected source you do not have.

The 1.3 README describes the current implementation as a PlayCanvas Engine 2.23.2 browser game with JavaScript in an HTML module and an external engine loaded from jsDelivr. Its documented features include:

- Six connected settlements: Sanjh Town; two cities, Nawanagar City and Fatehgarh City; and three villages, Chakk Dhaliwal, Bhagatpura, and Kalanpur.
- An extended road spine, rural fields, connectors, a canal crossing, pump-house area, and old canal weighbridge.
- Six taxi ranks, a fare/destination UI, and fast travel with a fade. The current taxis are static models, not driveable vehicles.
- Nineteen building-entry portals with small separately staged interiors, rather than seamless connected interiors.
- Named characters and side-character profiles including Baljit Kaur (Nav's mother), Gurdeep “Deep” Sandhu (childhood friend), Mehak Gill (reporter), and Iqbal Singh (taxi driver), plus residents and workers.
- A personal-story panel, local conversations, an evidence journal, and three connected cases.
- Save schema v11 and migration support from older save data.
- Procedural/stylised environment assets and scripted, low-cost NPC routines.

Treat this list as **documented baseline claims to verify in source**, not proof that every feature works. The previous 1.3 report noted that syntax/static checks passed but full browser rendering, complete campaign completion, taxi travel, building portals, NPC behaviours, and actual laptop FPS remained unverified because the PlayCanvas CDN did not load in the testing environment.

First inspect the actual source, map its architecture and save schema, and establish what works. Then implement the whole-game upgrade.

# 1. GAME IDENTITY — PRESERVE IT

**Title:** RAAH: The Unmarked Route  
**Setting:** Sanjh, a fictional contemporary district inspired by Punjab, India.  
**Genre:** First-person, single-player, open-world investigative story game.  
**Platform:** Desktop browser, initially Chrome and Edge.  
**Target hardware:** Ordinary laptop with integrated graphics.  
**Player character:** Nav Bedi, an independent field-verification specialist.  
**Core fantasy:** Explore a living district, form relationships, investigate conflicting accounts, reconstruct events, uncover interconnected cases, and see how the truth affects Nav's family, old friends, and the people of Sanjh.

This is a grounded human story. Do not replace it with supernatural powers, zombies, futuristic action, a GTA clone, or unrelated mechanics. The district should have a consistent fictional identity and believable regional details without implying that all real Punjabi places look identical.

# 2. THE ACTUAL GOAL: ONE COHERENT GAME, NOT A LIST OF HALF-FEATURES

Do not deliver a build that adds only new NPCs while neglecting the story, or only expands the map while taxi/interior/mission systems remain broken, or only adds UI panels without useful gameplay.

Work across the complete game in a coordinated pass. You may use internal milestones to organise work, but the final update must integrate all major systems together and provide a playable start-to-finish experience to the fullest extent feasible.

Prioritise in this order:

1. Preserve and stabilise existing 1.3 features.
2. Make the district, navigation, taxi travel, and building entry work together.
3. Make Nav and the side characters part of a real, structured personal story.
4. Develop the three cases into a coherent campaign with optional side stories and consequences.
5. Make NPCs, shops, interiors, vehicles, and settlements feel inhabited.
6. Improve the visual/audio presentation consistently, choosing stylised quality over fake realism when necessary.
7. Polish saving, browser compatibility, performance, and complete-game testing.

Do not stop after a planning document or a single subsystem. Implement directly.

# 3. THE COMPLETE DISTRICT — SIX SETTLEMENTS

The world must preserve the six-settlement plan:

- **Sanjh Town** — original market, chai stall, homes, records office, workshop and transport hub.
- **Nawanagar City** — larger city centre, residential districts, shops, clinics, offices, bus depot, cafés and transport connections.
- **Fatehgarh City** — a second distinct urban centre with its own layout, commercial area, civic spaces and residential streets.
- **Chakk Dhaliwal** — village streets, homes, agricultural edges and local residents.
- **Bhagatpura** — village hub, cooperative/agricultural activity and meaningful local landmarks.
- **Kalanpur** — village connected to the canal/field network and the larger mystery.

## World layout and navigation

- Build an intelligible connected district with primary roads, secondary roads, lanes, junctions, bridges, gates, paths and rural connectors.
- Make the two cities visibly and spatially different from the main town and each village. Differentiate their street widths, density, building types, landmarks, traffic context and layout—not just their signboards.
- Use believable scale, clear landmarks, walkable routes and useful lines of sight.
- Preserve the rural road, canal crossing, pump-house, old weighbridge and access-road clues.
- Implement a useful district map with settlement names, player position, taxi stands, entered/discovered locations, current objective and known landmarks. Do not reveal secret evidence on the map before the story permits it.
- The world should support exploration beyond the direct main-mission path: optional conversations, side objectives, discoverable interior locations, local activities and clues.
- Avoid empty acreage added only to make the map look large. Every district should contain meaningful navigable space, landmarks, people, or story context.
- Organise the world into sectors/cells or another lightweight method if needed. Avoid loading an unnecessarily huge set of assets simultaneously.
- Every taxi destination and door transition must place Nav in a navigable, collision-safe location with the correct story/save state.

# 4. TAXIS, VEHICLES AND TRAVEL

The 1.3 baseline documents six taxi stands and a fare-based fast-travel interface. Audit it and make the complete travel experience dependable.

## Taxi service

- Interact with a taxi driver or taxi stand; show destination, estimated fare, and current in-game cash.
- Use a confirmation step before charging money.
- Show a short transition/ride sequence or tasteful travel vignette, then arrive at the correct destination spawn.
- Never deduct a fare if the trip is cancelled or fails.
- Ensure every destination ID maps to a real configured settlement and valid spawn point. No undefined coordinates, wrong city spawns, falling through ground or spawning inside buildings.
- Keep case prerequisites intact. A taxi ride must not grant evidence, solve a mission, or silently skip story events.
- Add fare logic appropriate to distance or documented fixed fares, and handle insufficient funds clearly. Do not strand the player in a softlock; walking remains available.
- Give Iqbal Singh and any other taxi driver consistent identities and context-sensitive dialogue.

## Vehicles

- Preserve the existing taxis, buses, auto-rickshaws, tractors and other vehicles already placed in the district.
- Use coherent scaling, orientation, wheels/ground contact, collision decisions and appropriate parking positions.
- Static vehicles are acceptable if they are intentional and correctly integrated. Do not pretend they are drivable.
- If full vehicle driving can be implemented without destabilising the game, add one straightforward, optional vehicle system with basic acceleration, steering, braking, collision, enter/exit, and clear controls. Otherwise keep driving as a later feature and make taxi travel work fully now.
- Any moving traffic must be limited and purposeful, follow routes, stop appropriately, avoid permanent collisions and remain affordable for integrated graphics.

# 5. BUILDINGS, INTERIORS AND DAILY PLACES

The 1.3 build documents 19 enterable building portals and small furnished staging interiors. Preserve and improve all 19 configured entry points.

- Each marked door should lead to a correct, named, purpose-specific interior—not one generic room with a different label.
- Include relevant spaces: Nav's family home, shops, chai stall/related work spaces, workshop, clinic, reporter/newsroom or office, records room, village council/cooperative, café and other configured places.
- Furnish interiors with appropriate furniture, lighting, objects and entry/exit positions. Add inspectable objects or optional interactions where they help exploration or story.
- Include exit points inside each interior. Show an understandable prompt and ensure Nav returns outside at the correct door with the right orientation and no collision trap.
- Preserve portal transitions if true seamless interiors are too costly. Make portal transitions feel deliberate with a brief fade or camera transition. Do not claim seamless traversal when interiors are separate scenes.
- Avoid overlapping room geometry, inaccessible evidence, wrong vertical placement, floating furniture, broken door hitboxes or return portals that cannot be targeted.
- Make entry/exit safe during dialogue, pause, save/load and case changes.
- The family home must be a major story location, not just a room included to meet a count.

# 6. NAV BEDI — A REAL MAIN-CHARACTER ARC

Nav must feel like the protagonist of a story, not a camera that collects evidence. Expand the existing personal-story layer into a coherent arc, using the characters already established.

## Core characters

- **Nav Bedi:** an independent field-verification specialist returning after years away. Observant, practical, sometimes too trusting of official records, and personally conflicted about what evidence may do to the people he knows.
- **Baljit Kaur (mother):** connected to Nav's family home, memory, childhood, the family's papers and old local knowledge. She should have her own point of view, concerns, boundaries and story beats—not merely give quest exposition.
- **Gurdeep “Deep” Sandhu (childhood friend):** a workshop owner/friend with his own responsibilities and imperfect memory. The friendship should include warmth, discomfort about Nav's absence, disagreement, and opportunities to rebuild trust.
- **Mehak Gill (reporter):** careful with evidence, interested in the wider public consequences, and willing to challenge Nav's assumptions.
- **Iqbal Singh (taxi driver):** a recurring character with consistent routes, personal opinions, knowledge of travel times and limitations on what he could actually have seen.
- **Existing witnesses, workers, residents, officials, farmers, clinic staff, shopkeepers and village characters:** retain and expand the configured profiles from the actual source.

Characters must not all sound alike. Give important people distinct motivations, voices, memories, knowledge limits, and relationship histories. Avoid making every person part of a conspiracy.

## Personal story requirements

- Create a clear beginning, middle and end for Nav's personal arc, woven through the central investigation.
- The mother, Deep and Mehak should have multiple conversations at appropriate story moments rather than a single interaction each.
- Include character-specific optional scenes or tasks that reveal personal history through places and actions, not only dialogue panels.
- Include relationship state/flags where meaningful: trust, unresolved tension, willingness to share information, or willingness to help.
- Player decisions may change future dialogue, optional assistance, access, or the tone of the ending. Do not make every choice a simplistic good/bad morality score.
- Keep personal conversations separate from hard physical evidence. A remembered detail can create a lead without automatically proving the case.
- Avoid abrupt, unearned emotional turns. Use small moments, callbacks, disagreements and consequences so the relationships feel earned.
- Show the family house and familiar places as different from generic public spaces: objects, photos, papers and room details may evoke history.
- The opening needs to establish why Nav is back, what is personally at stake, and why this investigation matters to him.
- The ending should resolve the main mystery sufficiently while allowing the human and institutional consequences to remain nuanced.

# 7. THREE CASES INTO A PROPER STORY CAMPAIGN

Preserve the documented cases and connect them into a playable campaign:

## Case 001 — The Unmarked Route

The night-shift transport dispatcher disappears. Route information, tyre marks, the shift ledger, interviews and physical locations do not agree. Make the player understand the case goals, discover clues, compare sources, test explanations and reach a supported conclusion.

## Case 002 — A Boundary on Paper

A disputed boundary and access road connect a family's problem to older route records and the canal/weighbridge location. Include relevant locations, people, records, optional evidence, competing explanations, and a clear completion path. Do not treat a witness claim as unquestionable fact.

## Case 003 — The Last Dispatch

Bring the key evidence, route history and relationships together. Let the player reconstruct the most defensible timeline and decide how to handle/report the findings where appropriate. Provide a real ending with a debrief and character/world consequences. Do not fake a confession or reveal unsupported facts simply to force closure.

## Main/side mission system

- Every main mission has a clear narrative purpose, objective, required evidence/steps, fail/recovery conditions if relevant, completion state, and next lead.
- Add meaningful side cases in the cities, town and villages. Examples may include a repair-log discrepancy, a missing parcel, a disputed path, a public-works complaint, or a local person's unresolved concern—but integrate each with the game's grounded tone.
- Side content should sometimes deepen the district and characters without forcing every subplot to connect to the main conspiracy.
- Mission state must survive save/load. Repeating a conversation or examining a clue should not duplicate awards or corrupt quest state.
- Avoid softlocks: every mandatory clue, interview, door, taxi destination and case transition must remain reachable.
- Give players enough context to understand what they are trying to establish. Use world clues and dialogue rather than relying only on floating quest markers.
- Add callbacks and consequences for decisions without making branches impossible to test or maintain.

# 8. NPCS, CROWD LIFE AND BEHAVIOUR

The world needs people in the right places, not merely a count of spawned models.

- Keep NPCs distributed across all six settlements and important interiors.
- Include residents, shopkeepers, customers, workers, farmers, students/adults where appropriate, drivers, clinic staff, clerks, officials and other roles that make sense for each place.
- Ensure different appearances/clothing/body silhouettes where assets permit. If the assets are stylised, make them intentionally varied rather than pretending they are photorealistic.
- Provide useful ambient behaviour states: idle, walk to destination, pause, look around, interact with a prop, wait, talk to a character, respond briefly to Nav, and resume routine.
- Use tested waypoints or navigation. NPCs must not walk through walls, sink into ground, cross counters, block the player permanently or get stuck indefinitely.
- Do not make every NPC follow Nav, stare at the camera, trigger the same dialogue, or run the same animation in synchrony.
- Key side characters must have stable identities, schedules/locations or story gating, dialogue progression, and save-aware relationship/state flags.
- Ambient residents can provide local context, but must not provide inconsistent or omniscient information.
- Use lightweight AI: deterministic state machines and waypoint graphs are acceptable. No generative AI server is required.
- If full crowds are too expensive, use distance-based update rates and bounded population per zone. The district should feel lived in while preserving performance.
- The term “mobs” means ambient crowds/people here; do not add fantasy enemies or combat mobs.

# 9. INTERACTIONS, DIALOGUE AND EVIDENCE

The player should be able to talk to far more people than only the main witness, but each interaction needs a purpose.

- Build a consistent interaction resolver using distance, view direction, line of sight, type and state. Prioritise a clear target when evidence, NPCs, doors and taxis are close together.
- Aiming at an NPC and pressing E should talk only if the NPC is in range and available; doors enter/exit; taxis open the travel service; evidence records a clue; each should not accidentally trigger another object.
- Dialogue must have a reliable close/continue/back state and restore controls/pointer lock correctly.
- Use structured character-specific dialogue nodes and prerequisites. Do not let characters mention facts Nav has not learned or that they couldn't know.
- Record testimony as a separate source type, including who said it, the question/topic, the response, context and reliability limits where appropriate.
- Each physical clue has a stable ID, title, description, location, source type, status, relevant timing and optional connections.
- Repeated examination must be idempotent. No duplicate clues, repeated rewards or inconsistent counts.
- The journal should show collected evidence, interviews, active cases, unanswered questions, known destinations, story relationships and completed side content where relevant.
- The deduction system should explain why a hypothesis is supported or incomplete without revealing the answer automatically.
- Make interactions usable at ordinary laptop resolutions and with keyboard/mouse. Avoid tiny unreadable text or dependence on colour alone.

# 10. VISUAL DIRECTION — COHERENT STYLISED QUALITY IS ACCEPTABLE

Do not waste the whole task trying to force photorealism out of procedural boxes. Choose the best coherent look supported by available assets: high-quality stylised realism, a thoughtful low-poly art direction, or realistic asset-driven scenes where suitable assets genuinely exist.

Whichever style you choose, apply it consistently across the district, characters, props, UI, lighting and materials.

- The two cities, town and three villages need different silhouettes and spatial identities.
- Avoid repeating identical rectangles and only changing their colours.
- Use appropriate facade variations, balconies, shutters, doors, windows, rooflines, water tanks, utility details, weathered plaster, brick, metal grilles, signs, roads and drains.
- Make the chai stall read as a functioning chai business, with canopy/frame, counter, stove/kettle/pan, steel milk can, glass cups, jars, bench/stools, lighting and a vendor positioned behind the counter.
- Important human characters should look coherent and visibly human. Prefer appropriately licensed rigged GLB/glTF models and animation clips where access, licences, rig compatibility, and performance allow. If you cannot obtain them, use a consistent stylised character style and be honest about its limitations.
- Use purposeful material scale, roughness, contact shadows, consistent lighting and proper object grounding.
- Avoid heavy screen-grain as a substitute for material detail, excessive bloom/vignette, random clutter, broken proportions, floating objects and mismatched art styles.
- Give interior rooms a clear identity and adequate visual detail. The family house, clinic, workshop, office, café and cooperative should not look like the same empty box.
- Use camera compositions and sightlines to reveal landmarks and guide exploration without covering the screen in arrows.

# 11. AUDIO, ENVIRONMENT AND AMBIENCE

Add or improve a coherent soundscape using available/licensed audio:

- Distant traffic and occasional horns in appropriate locations.
- Footsteps and surface-aware feedback where practical.
- Birds, wind and outdoor ambience in rural spaces.
- Shop, workshop, clinic, office and chai-stall contextual sound loops.
- Subtle dialogue/interaction feedback.
- Indoor/outdoor volume differences and positional attenuation where supported.
- Optional restrained music only where it supports the narrative.
- Master/music/ambience/effects volume settings where feasible.

Do not autoplay loud sound before the player starts. If audio assets cannot be acquired, use a minimal tasteful procedural fallback or clearly document that audio is incomplete. Do not pretend generated placeholder tones are professional sound design.

Day/time/weather variation is optional and should only be added if it does not break clue timelines, visibility, NPC schedules or performance.

# 12. VEHICLES, CITY LIFE AND ACTIVITIES

Preserve current taxis, buses, auto-rickshaws, tractors and any other vehicles already in the world. Make their placement and scale coherent.

- Taxi travel must function reliably with valid destinations, fare confirmation, cash checks, safe arrival spawn points, cancel handling and no evidence/case skipping.
- Taxi drivers should be named/contextual where appropriate and remember only plausible information.
- Use vehicle type and density in the right locations: buses and auto-rickshaws in urban transport areas; tractors near rural/farm areas; parked scooters/bicycles around shops and homes.
- Add optional, low-cost local activities where useful: visit a shop, inspect an office board, ask for directions, explore a known location, speak to a resident, or perform a side task.
- Full driveable vehicles are optional unless they can be implemented and tested without destabilising the game. If included, provide clear controls, collisions, enter/exit logic and an actual functioning driving loop. Otherwise do not advertise static vehicles as drivable.

# 13. MAP, JOURNAL, HUD, MENUS AND SETTINGS

Keep the established interface style, improving consistency and usability rather than rebuilding it for decoration.

- Title/start screen and clear loading/error handling.
- In-game HUD with location/time/context only where useful.
- District map showing known/visited settlements, Nav's location, key discovered locations, active target and taxi stops.
- Evidence journal, interview records, personal-story panel, main/side mission list, deduction interface, and case debrief.
- Pause/resume, controls/help, settings, save/export/reset controls where present.
- FOV/mouse sensitivity, audio level and graphics quality controls where feasible.
- Keyboard/mouse navigation, readable text at laptop resolution, clear focus states, and no stuck pointer lock.
- Buttons and prompts must be genuinely functional. Remove or label unimplemented placeholders.
- Do not clutter the screen with constant markers or use a neon sci-fi style incompatible with the grounded game.

# 14. SAVE, MIGRATION AND DATA INTEGRITY

Inspect the actual baseline save schema. The 1.3 README documents schema v11 and migration from older data; verify this from source.

- Preserve migration for supported earlier versions.
- Version any new schema correctly; never invent the baseline version.
- Preserve campaign progress, evidence, testimonies, case status, taxi wallet, visited locations, relationship flags, discovered areas, settings and interior state where appropriate.
- Store game state—not live engine object references.
- Validate local data and any save file import. Do not execute imported data as code.
- Do not overwrite a newly imported save with stale startup state.
- Ensure a taxi/portal/case transition saves or restores coherent location and state.
- Provide a deliberate reset confirmation separate from ordinary loading.
- Provide portable export/restore where available, with a recovery path if browser storage fails.
- Do not silently erase player progress.

# 15. BROWSER TECHNICAL FOUNDATION

Preserve PlayCanvas Engine 2.23.2 and the existing JavaScript/HTML architecture unless there is a verified reason to change it.

- Handle engine/asset CDN failure with a clear message and retry path. Identify all network dependencies accurately.
- Handle resize, pointer lock, focus/blur, Escape, keyboard state clearing and pausing on tab loss.
- Avoid duplicate event handlers, global-state conflicts, repeated per-frame allocations, leaks and orphaned timers/listeners.
- Use clear data structures for settlements, doors/interiors, NPCs, cases, evidence, dialogue and side objectives.
- Avoid breaking every location when one settlement record changes; use stable IDs and validation.
- Handle missing assets explicitly. Include a manifest listing source, licence, format, size and intended use for externally obtained assets. Never invent a source or licence.
- Package every local dependency and asset when permitted. If an external CDN remains required, document that internet is required.

# 16. PERFORMANCE TARGET

The game must prioritise stability on an ordinary integrated-graphics laptop.

- WebGL 2 should remain the required baseline where compatible with the existing setup; do not require WebGPU for ordinary play.
- Keep Low/Medium/High presets functional if available: they must change real rendering costs while preserving core gameplay.
- Use efficient models/textures, reasonable draw calls, reuse, instancing where appropriate, asset compression, visible-zone/sector loading, and reduced update rates for distant NPCs where beneficial.
- Keep shadow-casting lights and effects restrained.
- Test scene load time, memory growth, character update load and interactions at representative viewpoints.
- Target stable approximately 30 FPS on the target laptop as a goal, not a claim. 60 FPS is a stretch goal.
- Never claim measured FPS without an actual runtime measurement on suitable hardware.

# 17. QA AND DEBUGGING — TEST THE WHOLE EXPERIENCE

A syntax check is necessary but not sufficient. Use a genuine browser/runtime and automation if available. If external engine loading is blocked, report the blocker and test all parts that can be tested locally without pretending the whole game ran.

Test all of these after implementation:

### Startup and controls
- Fresh start, start screen, game initialisation and visible failure message when engine/CDN unavailable.
- WASD, diagonal movement, sprint, mouse look, pointer lock, Escape, pause, resume, browser resize, tab switch and focus recovery.
- Collision/grounding and camera against representative walls, counters, fences, bridge parapets and building entrances.

### District and movement
- Visit all six settlements through valid roads and taxi travel.
- Confirm each map label matches the actual destination.
- Validate every taxi stand, fare, insufficient-funds handling, cancellation, travel completion and arrival position.
- Test the 19 configured building portals, enter/exit loops and story character targeting indoors.
- Ensure no routine transition leaves Nav inside geometry or blocks controls.

### Story and case progression
- Play Case 001 from starting state through supported conclusion.
- Unlock and play Case 002 through its intended completion path.
- Play Case 003 and reach the campaign ending if the source implements it.
- Test each required clue/interview, repeated interactions, optional dialogue, unsupported hypothesis, valid deduction, journal accuracy and debrief.
- Confirm personal-story scenes with Baljit, Deep and Mehak appear at the right points and do not conflict with main-case state.
- Verify side missions and NPCs don't reveal facts too early or count optional conversations as physical evidence.

### NPCs and interiors
- Sample NPC routines in all settlements, including city, town, village and selected interior contexts.
- Check that NPCs don't get permanently stuck, overlap constantly, walk through major walls, fall below ground or open the wrong dialogue.
- Repeatedly enter/exit buildings, open/close dialogue, open/close journal and pause/resume.

### Save system
- Save and reload a fresh game.
- Save after clue collection, testimony, case completion, taxi trip, visited location and relationship flag.
- Test supported migrations, malformed data, import/export, reset confirmation and recovery from failed writes.
- Ensure valid progress survives refresh and is not duplicated or silently cleared.

### Packaging and performance
- JavaScript syntax, HTML parsing, duplicate IDs, static DOM references, missing assets and archive integrity.
- Test at wide and narrow desktop viewports.
- Inspect console/network errors and actual rendered screenshots if the environment supports it.
- Measure actual performance if possible. Otherwise list it as NOT RUN/BLOCKED.

Every test must be recorded as **PASS**, **FAIL**, **NOT RUN**, or **BLOCKED**. Do not treat static presence of a function as proof that it works.

# 18. IMPLEMENTATION PROCESS — ONE WHOLE-GAME PASS

Follow this internal work sequence, but do not return after any single step:

1. Audit latest 1.3 source and verify documented features.
2. Back up original 1.3 and identify critical regressions.
3. Create a concise system dependency map and choose a compatible architecture for the complete project.
4. Fix reliability issues that affect multiple systems.
5. Integrate world/settlement layout, interiors, maps, and taxi travel so destinations match.
6. Integrate main character, side-character narrative, dialogue, relationships and mission state.
7. Integrate NPC routines, contextual interactions, vehicles and optional local activities.
8. Integrate cases, evidence, deductions, side quests, journal and campaign ending.
9. Improve art direction, key locations, environmental assets, human asset usage, animation and sound consistently.
10. Integrate saving/migration/settings across all new systems.
11. Test the full user journey and fix regressions.
12. Optimise, package and write honest documentation.

Do not ask me to approve minor design choices. Use professional judgement. If some features cannot reasonably be fully delivered in one execution, provide the most complete integrated game possible, clearly differentiate implemented systems from partial/planned ones, and do not falsely claim that the entire world is finished. Still address **all** major categories rather than spending the whole run on one feature.

# 19. FINAL DELIVERY — REQUIRED FILES

Return:

1. A runnable updated HTML build with a clear new version number (use **RAAH Personal Edition 1.4** unless the project/versioning state requires a different number; explain if changed).
2. The complete editable source and all local assets/configuration needed to run it.
3. A ZIP package containing the updated build, necessary assets, documentation, and untouched baseline backup.
4. README with exact launch instructions, controls, dependencies, browser requirements and troubleshooting.
5. Changelog compared directly with Personal Edition 1.3.
6. Asset manifest with verified asset sources/licences.
7. A test report for every category above, marked PASS/FAIL/NOT RUN/BLOCKED.
8. A system inventory showing for each feature: implemented and tested; implemented but runtime-unverified; partial; or not implemented.
9. Actual screenshots from the running game if the environment can render it. Never use concept art or generated imagery as fake gameplay screenshots.
10. Known limitations, especially external dependencies, asset placeholders, unverified runtime behaviours, and performance uncertainty.

Keep the baseline untouched. Do not silently erase saves or source history. Do not return only snippets or a plan.

# 20. DEFINITION OF SUCCESS

The updated RAAH should feel like one connected, personal, investigative adventure. A player can begin Nav's story, meet his mother and old friend, explore a distinct town/city/village district, speak to meaningful side characters and ambient residents, enter relevant buildings, use a taxi to travel correctly, follow main and optional storylines, gather and compare evidence, complete the three interconnected cases, reach an ending, and save/reload without losing progress.

The world must be large enough to support the six-settlement vision but purposeful rather than empty. NPCs must be present for reasons, not merely to inflate the count. Buildings must have spatial identity and interiors must support actual exploration. The story must combine the missing dispatcher, route/access-road history, family relationships and the consequences of revealing the truth in a coherent way.

Graphics may be stylised. Systems may be lightweight. The game does not need multiplayer, user accounts, live-service servers or an AI backend. It does need working mechanics, coherent geography, engaging characters, a real story, stable saves, consistent art direction, and honest testing.

**Do not focus on just one subsystem. Build the fullest, most cohesive version of the whole game that the existing project and available tools can support.**

# START NOW

Inspect the actual RAAH Personal Edition 1.3 source and all supplied project files. Confirm the baseline from the files. Then implement the integrated full-game upgrade, test what you can actually run, and return the full playable project with the required documentation and truthful test results.