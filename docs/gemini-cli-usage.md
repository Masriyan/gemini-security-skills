# Gemini CLI usage

This document explains how to use the installed skills during Gemini CLI
sessions.

## Discovery model

Gemini CLI discovers skills from several locations. In practical order for this
repository:

- User skills: `~/.gemini/skills/`.
- Workspace skills: `.gemini/skills/` inside the current project.
- Interoperable aliases: `~/.agents/skills/` and `.agents/skills/`.
- Extension skills: bundled under `skills/` inside an installed extension.

Each skill must be one directory deep and must contain a file named
`SKILL.md`.

Example:

```text
~/.gemini/skills/
├── go-programming/
│   └── SKILL.md
└── offensive-security/
    └── SKILL.md
```

## Manage skills in a session

Use these commands inside Gemini CLI:

```text
/skills list
/skills list nodesc
/skills reload
/skills disable offensive-security
/skills enable offensive-security
```

Use `/skills reload` after copying or editing skill files.

## Invoke skills naturally

Gemini CLI activates skills based on each skill's `name` and `description`.
You can rely on natural language or explicitly mention the skill by name.

Examples:

```text
Use go-programming to review this package for goroutine leaks.
Use soc-operations to triage this failed-login spike.
Use devsecops to harden this GitHub Actions pipeline.
Use prompt-enhancement to rewrite this vague agent prompt.
Use multilingual to localize this README into Indonesian.
```

## Combine skills

Complex tasks can benefit from multiple skills. State the order when the order
matters.

Examples:

```text
Use cybersecurity-partner first to threat model this service, then use
devsecops to turn the highest risks into CI/CD controls.
```

```text
Use malware-reverse-engineering to summarize this sandbox report, then use
soc-operations to create a triage note and hunting plan.
```

```text
Use prompt-enhancement to clarify this assessment prompt, then use
offensive-security to build a safe authorized test plan.
```

## Trust and consent

Gemini CLI treats skills as privileged context. Workspace skills may require the
workspace to be trusted before they load. When a skill activates, review the
skill name and path before approving activation.

Do not install skills from repositories you do not trust. A skill can influence
agent behavior and may include bundled resources.

## Updating installed skills

If you installed by copying folders, update manually:

```bash
cd /path/to/gemini-security-skills
git pull
cp -R skills/* ~/.gemini/skills/
```

Then run:

```text
/skills reload
```

If you installed as an extension, run:

```bash
gemini extensions update gemini-security-skills
```

Then restart Gemini CLI or run `/skills reload`.
