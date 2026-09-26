---
description: Derive the project's visual bible from the style preset and the story
---

Project directory: $ARGUMENTS

The visual bible is the rendering constitution for every image in this
project. It applies the configurable style preset — never hard-code a style —
and makes it specific to this story.

1. Read `context/style-preset.json`, `story/final.json`,
   `context/character-bible.json`, `context/object-bible.json` and
   `context/location-bible.json` in the project directory.
2. Derive the story-specific visual system: a named palette (concrete colours
   with usage notes, in the preset's palette direction), recurring visual
   motifs drawn from the story, and composition rules for the preset's aspect
   ratio.
3. Write `context/visual-bible.json` with exactly: `medium`, `rendering`,
   `palette` (array of ≥3 named colours with usage notes), `paper_texture`,
   `illustration_style`, `caption_typography`, `aspect_ratio`,
   `composition_rules` (array), `recurring_motifs` (array),
   `style_keywords` (array of ≥3 keywords every image prompt must include),
   `negative_keywords` (array — include the preset's `never` list),
   `source_preset` (the preset's `name`).

Output only the JSON file.
