# Troubleshooting

Use this guide when Gemini CLI does not load or activate a skill from
`https://github.com/Masriyan/gemini-security-skills`.

## Skills do not appear in `/skills list`

Check the installation path:

```bash
find ~/.gemini/skills -maxdepth 2 -name SKILL.md | sort
```

Expected result:

```text
~/.gemini/skills/go-programming/SKILL.md
~/.gemini/skills/offensive-security/SKILL.md
```

Fix common path mistakes:

- Wrong: `~/.gemini/skills/gemini-security-skills/go-programming/SKILL.md`.
- Right: `~/.gemini/skills/go-programming/SKILL.md`.
- Wrong: `~/.gemini/skills/go-programming/skill.md`.
- Right: `~/.gemini/skills/go-programming/SKILL.md`.

Then run:

```text
/skills reload
```

## A workspace skill does not load

Workspace skills live under `.gemini/skills/` in the current project.

Check:

```bash
find .gemini/skills -maxdepth 2 -name SKILL.md | sort
```

If the files exist but Gemini CLI does not load them, trust the workspace:

```text
/trust
```

Restart Gemini CLI or run:

```text
/skills reload
```

## A skill appears but does not activate

A skill activates when Gemini CLI matches the task to the `name:` and
`description:` metadata.

Use an explicit prompt:

```text
Use offensive-security to create an authorized assessment plan for my lab API.
```

If explicit invocation works but natural invocation does not, improve the
`description:` field in `SKILL.md` so it includes the missing task terms.

## YAML frontmatter errors

`SKILL.md` must start with frontmatter at the first byte of the file:

```yaml
---
name: go-programming
description: Go software engineering skill for implementation and review.
---
```

Common problems:

- A blank line before the first `---`.
- Missing closing `---`.
- Missing `name:` or `description:`.
- Tabs or malformed YAML.
- Folder name does not match the `name:` field.

## Remote install fails

If this command fails:

```bash
gemini skills install https://github.com/Masriyan/gemini-security-skills
```

Use the extension install command for the full multi-skill bundle:

```bash
gemini extensions install https://github.com/Masriyan/gemini-security-skills --consent
```

If extension installation is not available, use the manual clone-and-copy
method:

```bash
git clone https://github.com/Masriyan/gemini-security-skills.git
cd gemini-security-skills
mkdir -p ~/.gemini/skills
cp -R skills/* ~/.gemini/skills/
```

The extension or manual method is best for this repository because it contains
multiple skills rather than a single root skill.

## Skill behavior seems too broad

Tighten the skill description and body:

- Add specific trigger contexts to `description:`.
- Add clear non-goals.
- Add safety boundaries.
- Add expected output sections.
- Avoid vague persona language.

For cyber security skills, keep authorization and defensive outcome language in
the description so Gemini CLI sees it before activation.

## Skill behavior seems too narrow

Broaden the skill description:

- Add relevant file types.
- Add common task names.
- Add related workflows.
- Add synonyms users naturally type.

Example for SOC work:

```yaml
description: Security Operations Center skill for alert triage, detection
  engineering, incident response, log analysis, threat hunting, SIEM queries,
  EDR investigation, timeline building, IOC handling, escalation notes,
  containment recommendations, and analyst-ready reporting.
```
