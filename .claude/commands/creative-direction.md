---
description: Derive the creative direction for a story project from its high-level request
---

Project directory: $ARGUMENTS

1. Read `project.json` (the `request` field) and
   `context/input-analysis.json` in the project directory.
2. Respect the input analysis: every element in `locked` must be carried
   through from `provided` — normalise wording, never override the substance.
   You make fresh decisions only for the elements in `gaps`, and they must be
   coherent with what the user provided.
3. Make the creative decisions this story needs: audience, theme, emotional
   tone, primary and secondary emotion, relationship (type + participants +
   rationale — the relationship must emerge from the emotional meaning, per
   CLAUDE.md; do not reach for a banned default), setting, conflict, metaphor
   (if one serves the story), narrative structure, ending mechanism, duration
   in seconds (from the request, default 60), scene count appropriate to that
   duration, and pacing.
4. Write your decisions to `context/creative-direction.json` in the project
   directory as a single JSON object with exactly these keys: `request`,
   `audience`, `theme`, `emotional_tone`, `primary_emotion`,
   `secondary_emotion`, `relationship` (object: `type` — one of
   `human+human|human+animal|human+object|human+place|human+memory|human+reflection|human+shadow|human+younger_self|human+future_self|animal+animal|object+object|mixed`
   — `participants` array of strings, `rationale`), `setting`, `conflict`,
   `metaphor`, `narrative_structure`, `ending_mechanism`,
   `duration_seconds` (integer), `scene_count` (integer), `pacing`, `notes`.

Output only the JSON file. Do not create any other files.
