---
description: Score every concept and select the strongest for this creative direction
---

Project directory: $ARGUMENTS

1. Read `context/creative-direction.json` and `story/concepts.json` in the
   project directory.
2. Evaluate every concept honestly — do not inflate scores. Score each 1–5 on:
   `originality`, `emotional_authenticity`, `visual_potential`, `audience_fit`.
   A concept that leans on a cliché scores low on originality even if well
   executed.
3. Select the winner on merit, not order. Write
   `story/selected-concept.json`:
   `{"selected_id": "...", "rationale": "...", "evaluation": [{"id", "scores": {originality, emotional_authenticity, visual_potential, audience_fit}, "total", "notes"}, ...]}`
   with one evaluation entry per concept and `total` the sum of its four scores.

Output only the JSON file.
