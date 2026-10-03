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
3. Pick a fresh combination before deciding the rest (see the inspiration
   library in CLAUDE.md): one *territory* × one *borrowed film/book lens* × one
   precise modern conflict × a non-obvious relationship duo. Combine
   unexpectedly, avoid the obvious pairing, and never reach for a banned
   default. Invent a specific hook — a one-line premise, not a genre — and
   record the chosen lens and why it fits in `notes`.
4. Make the creative decisions this story needs: audience, theme (the chosen
   territory, made specific), emotional tone, primary and secondary emotion,
   relationship (type + participants + rationale — it must emerge from the
   emotional meaning, per CLAUDE.md), setting, conflict (concrete and modern —
   a real number, object, or unanswered message, not a general sadness),
   metaphor (the borrowed lens, felt not quoted), narrative structure (default
   to the emotional arc in CLAUDE.md, shaped to the duration), ending mechanism,
   duration in seconds (from the request, default 60), scene count appropriate
   to that duration, and pacing.
5. Write your decisions to `context/creative-direction.json` in the project
   directory as a single JSON object with exactly these keys: `request`,
   `audience`, `theme`, `emotional_tone`, `primary_emotion`,
   `secondary_emotion`, `relationship` (object: `type` — one of
   `human+human|human+animal|human+object|human+place|human+memory|human+reflection|human+shadow|human+younger_self|human+future_self|animal+animal|object+object|mixed`
   — `participants` array of strings, `rationale`), `setting`, `conflict`,
   `metaphor`, `narrative_structure`, `ending_mechanism`,
   `duration_seconds` (integer), `scene_count` (integer), `pacing`, `notes`.

Output only the JSON file. Do not create any other files.
