# AI Content Creation Skills

Reusable skills for AI content-creation workflows.

## Repository layout

Each distributable skill belongs in its own folder:

```text
skills/
  example-skill/
    SKILL.md
    agents/
      openai.yaml
    scripts/        # optional
    references/     # optional
    assets/         # optional
```

A skill is installable when its folder contains a valid `SKILL.md` with clear triggering metadata and operating instructions.

## Knowledge base and repository

- **ima knowledge base**: onboarding notes, usage instructions, examples, and searchable reference material.
- **This repository**: version-controlled, downloadable Skill packages.

Use the repository URL when an agent needs a Skill package; use the knowledge-base link when it needs product guidance or supporting context.

## Contributions

Add or update a Skill in its own folder under `skills/`. Keep each `SKILL.md` concise and include only the resources needed to run that Skill.
