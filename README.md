# story-forge

Autonomous visual-story production engine — a module of the
[Creative Minds](https://github.com/AK1699/creative-minds) ecosystem.

Given a high-level request ("a 60-second emotional story for Gen-Z"), Story
Forge derives the creative direction, generates and evaluates concepts, drafts
the story, and gates it through a critic/rewrite loop until it passes the
Story Quality Gate. Later phases add bibles (character/animal/object/location/
visual), scene planning, captions, and image prompts.

It is not run directly. The Creative Minds orchestrator invokes its stage
commands headlessly (`claude -p "/<stage> <project-dir>"`), and all state
lives in the project directory passed as the argument. The stage contract is
declared in [`module.json`](module.json); the creative rules the stages obey
are in [`CLAUDE.md`](CLAUDE.md).
