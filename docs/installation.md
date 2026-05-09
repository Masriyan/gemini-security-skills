# Installation guide

This guide explains how to install Gemini Security Skills into Gemini CLI at
user scope or workspace scope. The repository URL used by all examples is:

```text
https://github.com/Masriyan/gemini-security-skills
```

## Requirements

Install the required tools before installing the skills:

- Node.js with `npm`.
- Gemini CLI.
- `git` for cloning the repository.
- A trusted terminal environment because skills can provide instructions and
  bundled resources to the agent.

Install Gemini CLI with `npm`:

```bash
npm install -g @google/gemini-cli
```

Start Gemini CLI once to complete authentication:

```bash
gemini
```

## Recommended extension installation

Use extension installation when you want the complete multi-skill bundle. This
repository includes `gemini-extension.json` and a top-level `skills/` directory,
which is the Gemini CLI extension layout for bundled Agent Skills.

Run:

```bash
gemini extensions install https://github.com/Masriyan/gemini-security-skills --consent
```

Restart Gemini CLI after installation. Then verify:

```text
/extensions list
/skills list
```

Use this update command when you installed as an extension:

```bash
gemini extensions update gemini-security-skills
```

## Direct global skills installation

Use global installation when you want these skills available in every project.
Gemini CLI discovers user skills under `~/.gemini/skills/`.

Run these commands:

```bash
git clone https://github.com/Masriyan/gemini-security-skills.git
cd gemini-security-skills
mkdir -p ~/.gemini/skills
cp -R skills/* ~/.gemini/skills/
```

Start or reload Gemini CLI:

```bash
gemini
```

Inside Gemini CLI, run:

```text
/skills list
```

If Gemini CLI was already open, run:

```text
/skills reload
```

## Workspace installation

Use workspace installation when you want the skills active only for one
project. Gemini CLI discovers workspace skills under `.gemini/skills/` in the
current project.

From the target project root, run:

```bash
mkdir -p .gemini/skills
cp -R /path/to/gemini-security-skills/skills/* .gemini/skills/
```

If your workspace is not trusted, run `/trust` in Gemini CLI and restart the
session. Workspace skills are only useful when Gemini CLI can load project
resources safely.

## Link for development

Use linking when you are editing a local skill and want Gemini CLI to see
changes without copying files repeatedly.

Link individual skills:

```bash
cd /path/to/gemini-security-skills
gemini skills link ./skills/go-programming
gemini skills link ./skills/python-programming
gemini skills link ./skills/offensive-security
```

Repeat the command for each skill you actively develop. Then run `/skills
reload` inside Gemini CLI.

## Remote install command

Newer Gemini CLI builds expose `gemini skills install` for remote skill
repositories and local skill packages:

```bash
gemini skills install https://github.com/Masriyan/gemini-security-skills
```

This repository is a multi-skill collection. Prefer `gemini extensions install`
for the full bundle. If your Gemini CLI version expects `gemini skills install`
to target one skill at a time, use the extension install or clone-and-copy
method instead.

## Verify installation

Use these checks after installation:

```text
/skills list
/skills list nodesc
```

Then invoke a skill naturally:

```text
Use the Go programming skill to review this package for race conditions.
Use the SOC operations skill to triage this alert.
Use the malware reverse engineering skill to summarize this sandbox report.
```

If a skill does not appear, check that:

- The file is named exactly `SKILL.md`.
- The skill path is one directory deep under `~/.gemini/skills/` or
  `.gemini/skills/`.
- The YAML frontmatter starts at the first line of `SKILL.md`.
- The frontmatter contains `name:` and `description:`.
- You restarted Gemini CLI or ran `/skills reload`.
