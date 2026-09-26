---
description: Generate several genuinely distinct story concepts for the creative direction
---

Project directory: $ARGUMENTS

1. Read `context/creative-direction.json` in the project directory.
2. Generate 4 genuinely distinct story concepts that honour the creative
   direction. Distinct means different premises, not one idea reskinned four
   times — vary at least the relationship dynamic, the conflict, and the
   ending mechanism across concepts. Respect every banned default and banned
   message in CLAUDE.md. Each concept must be visually tellable in short-form
   vertical video.
3. Write `story/concepts.json` in the project directory:
   `{"concepts": [...]}` where each concept has exactly: `id` (e.g. "C1"),
   `title`, `logline` (one sentence), `relationship`, `conflict`, `metaphor`,
   `ending_mechanism`, `why_original` (what separates this from the generic
   version of the same idea).

Output only the JSON file.
