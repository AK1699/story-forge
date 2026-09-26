---
description: Generate one self-contained image prompt per scene for an external image module
---

Project directory: $ARGUMENTS

The consumer of these files is an external image-generation module that reads
NOTHING else — not the story, not the scenes, not the bibles. Each prompt file
must therefore be completely self-contained.

1. Read, in the project directory: every `scenes/scene-*.json`,
   `context/visual-bible.json`, and all entity bibles.
2. For each scene, write `prompts/prompt-001.json`, `prompts/prompt-002.json`,
   … (zero-padded, one per scene, same numbering) with exactly:
   - `scene_number`
   - `prompt` — the complete positive prompt as one string: subject(s) with
     their bible attributes embedded VERBATIM (age, face, hair, clothing,
     markings, object colour/condition as of this scene…), action,
     expression, setting with its bible description, time of day, weather,
     lighting, camera shot/angle/composition, then the full visual style
     (medium, rendering, palette, paper texture, illustration style,
     `style_keywords`). No references like "the girl from scene 3" — an
     image model has no memory between scenes; repetition of identical
     descriptors IS the continuity mechanism.
   - `negative_prompt` — the visual bible's `negative_keywords` plus anything
     this scene must avoid. Always exclude text/lettering in the image.
   - `aspect_ratio` — from the visual bible.
   - `caption` — the scene's caption verbatim (empty if none). Captions are
     overlaid downstream; the image itself contains no text.
   - `caption_style` — the visual bible's `caption_typography`.
   - `continuity_anchors` — the exact visual facts that must match
     neighbouring scenes (character descriptors, object condition, light),
     stated as short strings.
   - `source_scene` — e.g. "scenes/scene-004.json".

Use identical wording for the same entity's descriptors across all prompts.
Output only the JSON files.
