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

## Stages (Phase 1)

| Command | Reads | Writes |
| --- | --- | --- |
| `/context-analyzer` | project.json | context/input-analysis.json |
| `/creative-direction` | project.json, input-analysis | context/creative-direction.json |
| `/concepts` | creative-direction | story/concepts.json |
| `/select-concept` | creative-direction, concepts | story/selected-concept.json |
| `/story-draft` | creative-direction, selected-concept | story/draft.json |
| `/story-critic` | creative-direction, draft | story/critique.json |
| `/story-rewrite` | creative-direction, draft, critique | story/draft.json (version+1) |

Later phases add: bibles (character/animal/object/location/visual), scene
planning, captions, image prompts. Do not produce those yet.
