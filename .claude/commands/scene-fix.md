---
description: Regenerate only the scenes that failed the scene gate
---

Project directory: $ARGUMENTS

Regenerate ONLY what failed — never touch passing scenes.

1. Read `reports/scene-critique.json` in the project directory. The scenes to
   fix are those with `verdict: "fail"`; apply their `required_changes` and
   resolve their blocker/major issues. Also read the failed scenes' files,
   their immediate neighbours, `context/continuity-state.json` and all bibles.
2. Rewrite each failed scene file in place (same filename, same structure,
   same schema as before). The fixed scene must still inherit the previous
   scene's end state and hand the next scene exactly what it already expects —
   if you change something a later scene depends on, prefer a fix that
   preserves the handoff.
3. Update the affected entries in `context/continuity-state.json` so the
   timeline matches the fixed scenes. Leave all other entries untouched.

Output only the modified JSON files.
