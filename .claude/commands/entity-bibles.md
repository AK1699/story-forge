---
description: Create the character, animal, object and location bibles from the final story
---

Project directory: $ARGUMENTS

Continuity is a hard requirement: every scene and every image prompt will copy
these attributes verbatim. Be concrete and visual — "mid-60s, deep smile
lines, wire-rimmed glasses" beats "an old man". Invent the specifics the story
implies but does not state.

1. Read `story/final.json` and `context/creative-direction.json` in the
   project directory.
2. Write four files to `context/` in the project directory:
   - `character-bible.json` — `{"characters": [...]}`, each with `id` (e.g.
     "CHAR-1"), `name`, `role`, `age`, `face`, `hair`, `clothing` (note any
     deliberate changes), `accessories`, `body`, `demeanour`.
   - `animal-bible.json` — `{"animals": [...]}`, each with `id`, `name`,
     `species`, `size`, `markings`, `coat`, `distinctive_features`, `role`.
     Empty array if the story has no animals.
   - `object-bible.json` — `{"objects": [...]}` for story-significant objects,
     each with `id`, `name`, `shape`, `colour`, `condition` (at story start),
     `distinctive_marks`, `state_changes` (array of `{scene_number, change}`
     for deliberate condition changes — use the story's beat progression),
     `role`. Empty array only if truly no significant objects.
   - `location-bible.json` — `{"locations": [...]}` (at least one), each with
     `id`, `name`, `description` (architecture, furniture, geography — the
     fixed physical facts), `lighting`, `season`, `weather_default`,
     `time_variants`.

Output only these four JSON files.
