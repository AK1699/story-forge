---
description: Write the full story draft from the selected concept
---

Project directory: $ARGUMENTS

1. Read `context/input-analysis.json` and `context/creative-direction.json`
   in the project directory.
   - If the input mode is `auto` or `idea`: also read
     `story/selected-concept.json` and `story/concepts.json`, and work from
     the selected concept.
   - If the input mode is `story`: there are no concepts — work directly from
     the user's narrative in the input analysis (`provided.story_text` /
     `provided.premise`). Preserve their characters, events and meaning; your
     job is to structure it into beats, deepen it, and fill the gaps — not to
     rewrite it into a different story.
2. Write the complete story for the target duration. It must be visually
   tellable: think in beats a camera can show. Not every beat needs dialogue —
   prefer behaviour, silence, absence, symbolism, environmental change. The
   ending must be earned by the story, and the message must not be a
   motivational cliché (see CLAUDE.md).
3. Write `story/draft.json` in the project directory with exactly:
   `version` (integer, 1 for a first draft), `title`, `logline`,
   `narrative_structure`, `beats` (array, minimum 3, each with `beat` — a
   short name — `summary`, `emotional_purpose`, and `visual_storytelling` —
   how it communicates without words where applicable), `story_text` (the
   full prose story), `ending`, `message`.

Output only the JSON file.
