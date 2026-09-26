# story-forge

Story Forge is an autonomous visual-story production engine, not a story-writing
assistant. It is a module of the Creative Minds ecosystem: the orchestrator
invokes its stage commands headlessly, passing a project directory as the
argument. Project files are the single source of truth — always read your
inputs from the project directory and write your output there; never rely on
anything outside it.

## I/O contract

- Every stage command receives one argument: the absolute path to a project
  directory (`.../projects/STORY-NNNN`).
- Read only the input files your stage declares in `module.json`. Write only
  your declared output file, as JSON matching its schema in
  `creative-minds/schemas/`. No prose around it, no extra files.
- If the invocation includes validation errors from a previous attempt, fix
  exactly those errors.

## Input modes

The user may provide anything from a one-line brief to a complete story; never
force them to start from zero. `/context-analyzer` classifies the request —
`auto` (invent everything), `idea` (develop a given premise), `story` (a
narrative was supplied) — and records `locked` elements versus `gaps`. Every
downstream stage must preserve locked elements and decide only the gaps. In
`story` mode the orchestrator skips concept generation, and the draft stage
structures and completes the user's narrative rather than rewriting it.

## Creative rules (apply to every stage)

**Stories are for short-form vertical video.** They must be original,
emotionally authentic, visually understandable, concise, memorable, and
relatable to a modern audience. Emotion must be communicable *visually*.

**The relationship emerges from the emotional meaning of the story — never
from a template.** Choose from the full space: human+human, human+animal,
human+object, human+place, human+memory, human+reflection, human+shadow,
human+younger/future self, animal+animal, object+object, mixed. Justify the
choice in writing wherever the schema has a rationale field.

**Banned defaults — do not produce these unless the request explicitly asks:**
- boy + wise old man
- generic motivational story
- generic talking animal
- generic friendship story
- generic "never give up" arc

**Banned messages (and close paraphrases):** "Never give up." "Believe in
yourself." "Everything happens for a reason." The ending's meaning must be
*earned* by the specific story, not appended to it.

**Not every scene needs dialogue.** Prefer communicating through behaviour,
silence, absence, visual symbolism, repetition, environmental change, objects,
composition, facial expression, animal behaviour.

**Continuity is a hard requirement.** Scenes are frames of one continuous
film. The bibles (character/animal/object/location/visual) are persistent
project state: define an attribute once, then reuse it verbatim — never
reinvent age, face, hair, clothing, markings, object condition, architecture,
weather, season, light or style per scene. Scenes reference bible entries by
id; image prompts embed the bible descriptors word-for-word, because repeated
identical wording is the only continuity mechanism an image model has.

**Captions are part of the storytelling system**, generated with scene
planning, in one consistent voice: concise, non-redundant with the visual,
contributing emotional or narrative information. Scenes that speak for
themselves get an empty caption.

**The visual style is configurable, never hard-coded** — it comes from the
project's `context/style-preset.json`, applied via the visual bible.

## Stages

| Command | Reads | Writes |
| --- | --- | --- |
| `/context-analyzer` | project.json | context/input-analysis.json |
| `/creative-direction` | project.json, input-analysis | context/creative-direction.json |
| `/concepts` | creative-direction | story/concepts.json |
| `/select-concept` | creative-direction, concepts | story/selected-concept.json |
| `/story-draft` | creative-direction, selected-concept | story/draft.json |
| `/story-critic` | creative-direction, draft | story/critique.json |
| `/story-rewrite` | creative-direction, draft, critique | story/draft.json (version+1) |
| `/entity-bibles` | final, creative-direction | context/{character,animal,object,location}-bible.json |
| `/visual-bible` | final, style-preset, entity bibles | context/visual-bible.json |
| `/scene-planning` | final, direction, all bibles | scenes/scene-*.json, context/continuity-state.json |
| `/scene-critic` | scenes, bibles, continuity | reports/scene-critique.json |
| `/scene-fix` | critique, failed scenes, bibles | scenes/scene-*.json (failed only), continuity-state |
| `/image-prompts` | scenes, all bibles | prompts/prompt-*.json |

Story Forge ends at image prompts. Image generation belongs to image-forge —
never generate or fetch images.
