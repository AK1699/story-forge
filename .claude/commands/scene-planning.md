---
description: Plan the full scene sequence with captions and continuity state
---

Project directory: $ARGUMENTS

You are planning frames of one continuous film, not a collection of unrelated
images. Work strictly in order: each scene must inherit the state the previous
scene ended in.

1. Read, in the project directory: `story/final.json`,
   `context/creative-direction.json`, and all bibles
   (`character-bible.json`, `animal-bible.json`, `object-bible.json`,
   `location-bible.json`, `visual-bible.json`). The scene count is
   `scene_count` in the creative direction; scene durations must sum to
   approximately `duration_seconds`.
2. Plan the scenes IN ORDER. Reference bible entries by `id` only — never
   restate or reinvent their attributes. Respect the object bible's
   `state_changes`. Vary camera shots and angles purposefully. Where the
   story communicates without words, let it: behaviour, silence, absence,
   symbolism, environmental change.
3. Captions are part of the plan (write them per scene, as one sequential
   voice): concise, natural when read in sequence, adding emotional or
   narrative information the visual does not already state. Leave `caption`
   empty for scenes that speak for themselves — not every scene needs text.
4. Write one file per scene: `scenes/scene-001.json`, `scenes/scene-002.json`,
   … (zero-padded to 3 digits) with exactly: `scene_number`,
   `duration_seconds`, `narrative_purpose`, `emotional_purpose`, `location`
   (location bible id), `time_of_day`, `weather`, `characters` (array of
   `{id, state, expression}`), `animals` (array of `{id, behaviour}`),
   `objects` (array of `{id, state}`), `actions` (array), `camera`
   (`{shot, angle, composition}`), `visual_metaphor` (optional), `caption`,
   `continuity` (`{carries_from_previous, must_match}` — the exact facts this
   scene inherits and must not contradict).
5. Then write `context/continuity-state.json`:
   `{"timeline": [{"scene_number", "end_state", "changes_from_previous"}, ...]}`
   — one entry per scene, describing the world state when that scene ends
   (who/what is where, object conditions, time, weather, light).

Output only these JSON files.
