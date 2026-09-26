---
description: Classify the user's request (auto/idea/story) and lock the elements they provided
---

Project directory: $ARGUMENTS

The user should never be forced to start from zero — they may give anything
from a one-line brief to a complete story. Your job is to work out what they
gave and what Story Forge must fill in.

1. Read `project.json` in the project directory — the `request` field.
2. Classify the input mode:
   - `auto` — only constraints/preferences given (audience, duration, tone),
     no premise. Example: "Create a unique emotional story for Gen-Z."
   - `idea` — a premise or seed image given, but not a worked-out narrative.
     Example: "A girl keeps leaving an umbrella at a bus stop."
   - `story` — a substantive narrative with characters and events. The user's
     story must be preserved and completed, NOT rewritten blindly.
3. Extract every creative element the request actually contains into
   `provided` (theme, emotion, relationship, characters, setting, conflict,
   metaphor, ending, premise, story_text, audience, duration, ...). Do not
   invent entries — only what is genuinely in the request. List those element
   names in `locked`; list the elements Story Forge must decide in `gaps`.
4. Write `context/input-analysis.json` in the project directory with exactly:
   `mode` ("auto" | "idea" | "story"), `rationale`, `provided` (object),
   `locked` (array of element names), `gaps` (array of element names).

Output only the JSON file.
