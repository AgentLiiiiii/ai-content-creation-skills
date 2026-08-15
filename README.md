# AI Content Creation Skills

Reusable skills for AI content-creation workflows.

## Skill catalog

| Skill | Purpose | Install path |
| --- | --- | --- |
| Video Prompt Craft | Turn a static storyboard and emotional target into image-to-video motion prompts and camera guidance. | `skills/video-prompt-craft` |
| Performer Prompt Engineer | Convert storyboard-based performance analysis into character-performance video prompts. | `skills/performer-prompt-engineer` |
| Character Designer | Develop character biographies, look-reference prompts, costume/prop support, and character cards from a story or script. | `skills/character-designer` |

Ask an Agent to inspect the relevant `SKILL.md` before installation. For example: “Find the Skill for character performance and install `skills/performer-prompt-engineer`.”

## Repository layout

Each distributable skill belongs in its own folder:

```text
skills/
  skill-name/
    SKILL.md
    references/     # optional
    scripts/        # optional
    assets/         # optional
```

A skill is installable when its folder contains a valid `SKILL.md` with clear triggering metadata and operating instructions.

## Knowledge base and repository

- **ima knowledge base**: onboarding notes, usage instructions, examples, and searchable reference material.
- **This repository**: version-controlled, downloadable Skill packages.

Use the repository URL when an agent needs a Skill package; use the knowledge-base link when it needs product guidance or supporting context.

## Contributions

Add or update a Skill in its own folder under `skills/`. Keep each `SKILL.md` concise and include only the resources needed to run that Skill.
