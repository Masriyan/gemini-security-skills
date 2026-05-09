# Development and maintenance

This document explains how to maintain the skills in
`https://github.com/Masriyan/gemini-security-skills`.

## Skill structure

Each skill uses this structure:

```text
skills/
└── skill-name/
    ├── SKILL.md
    └── agents/
        └── openai.yaml
```

`SKILL.md` is the core file. It must start with YAML frontmatter:

```yaml
---
name: skill-name
description: Clear trigger description for when the skill should be used.
---
```

The body should contain only operational guidance that helps the agent perform
the task. Keep the file concise enough to load into context when activated.

## Naming rules

Use these rules for skill names:

- Use lowercase letters, digits, and hyphens only.
- Keep names short and descriptive.
- Match the folder name to the `name:` field.
- Avoid spaces, underscores, and uppercase letters.

## Description quality

The `description:` field is the main trigger. It should include:

- What the skill does.
- File types, domains, or task contexts that should activate it.
- Important boundaries, especially for dual-use security work.

Do not hide trigger details only in the body. Gemini CLI sees the name and
description before it decides whether to activate the skill.

## Writing style

Write skill instructions as direct operational guidance:

- Use imperative language.
- Prefer workflows and checklists.
- Avoid generic explanations the model already knows.
- Include safety boundaries where misuse is plausible.
- Keep examples short and realistic.

## Validation

Validate every skill after editing:

```bash
python /home/sudo3rs/.codex/skills/.system/skill-creator/scripts/quick_validate.py go-programming
```

Validate all extension skills from this repository root:

```bash
for d in skills/*/; do
  [ -f "$d/SKILL.md" ] && python /home/sudo3rs/.codex/skills/.system/skill-creator/scripts/quick_validate.py "${d%/}"
done
```

If that validator is not available, manually check:

- `SKILL.md` exists.
- Frontmatter starts at line 1.
- `name:` and `description:` exist.
- Folder name matches `name:`.
- YAML delimiters are exactly `---`.

## Release checklist

Before publishing updates:

- Run validation for all skills.
- Search for leftover placeholders.
- Search for stale repository URLs.
- Verify README installation commands.
- Verify `gemini-extension.json` remains valid JSON.
- Check that security skills preserve authorization boundaries.
- Confirm every Markdown link resolves.

Useful commands:

```bash
rg -n "TODO|\\[TODO|github.com" .
find . -maxdepth 3 -type f | sort
```

All GitHub repository links should point to:

```text
https://github.com/Masriyan/gemini-security-skills
```

## Adding a new skill

Follow this process:

1. Create a new folder with a lowercase hyphenated name.
2. Add `SKILL.md` with valid frontmatter.
3. Write a precise `description:` field.
4. Add operational instructions and safety boundaries.
5. Add `agents/openai.yaml` if UI metadata is needed.
6. Place the skill under `skills/<skill-name>/` for extension installation.
7. Update `README.md`, `docs/skill-catalog.md`, and installation commands.
8. Validate the skill.
