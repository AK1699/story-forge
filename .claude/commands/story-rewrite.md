---
description: Rewrite the story draft to resolve the critic's required changes
---

Project directory: $ARGUMENTS

1. Read `context/creative-direction.json`, `story/draft.json` and
   `story/critique.json` in the project directory.
2. Rewrite the draft to resolve every entry in the critique's
   `required_changes` and every blocker/major issue. Address the root cause —
   do not paper over a structural problem with a line edit. Preserve what the
   critique did not object to; this is a rewrite of the same story, not a new
   concept.
3. Overwrite `story/draft.json` with the same structure as before
   (`version`, `title`, `logline`, `narrative_structure`, `beats`,
   `story_text`, `ending`, `message`) and `version` incremented by 1.

Output only the JSON file.
