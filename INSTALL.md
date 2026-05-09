# Install

This document gives direct installation commands for
`https://github.com/Masriyan/gemini-security-skills`.

## Recommended install: Gemini CLI extension

Use this method for the complete bundle. The repository includes
`gemini-extension.json` and a top-level `skills/` directory, which lets Gemini
CLI load all bundled Agent Skills from one extension.

```bash
gemini extensions install https://github.com/Masriyan/gemini-security-skills --consent
```

Restart Gemini CLI after installation, then verify:

```text
/extensions list
/skills list
```

Update the extension later with:

```bash
gemini extensions update gemini-security-skills
```

## Manual global install

Use this method when extension installation is unavailable or when you want
plain skill folders under your user profile.

```bash
git clone https://github.com/Masriyan/gemini-security-skills.git
cd gemini-security-skills
mkdir -p ~/.gemini/skills
cp -R skills/* ~/.gemini/skills/
```

Reload Gemini CLI:

```text
/skills reload
```

## Manual workspace install

Use this method when you want the skills active only inside one project.

```bash
git clone https://github.com/Masriyan/gemini-security-skills.git /tmp/gemini-security-skills
cd /path/to/your/project
mkdir -p .gemini/skills
cp -R /tmp/gemini-security-skills/skills/* .gemini/skills/
```

If Gemini CLI does not load workspace skills, trust the workspace and reload:

```text
/trust
/skills reload
```

## Development link install

Use linking while editing skills locally:

```bash
git clone https://github.com/Masriyan/gemini-security-skills.git
cd gemini-security-skills
gemini skills link ./skills/go-programming
gemini skills link ./skills/offensive-security
gemini skills link ./skills/malware-reverse-engineering
```

Repeat the link command for each skill you want to test.

## Verification checklist

After installation, confirm these points:

- `/skills list` shows the expected skill names.
- Every skill path contains a `SKILL.md` file.
- The skill folders are one directory deep under `~/.gemini/skills/`,
  `.gemini/skills/`, or the extension `skills/` directory.
- Gemini CLI was restarted or `/skills reload` was run.
- Workspace installs are inside a trusted workspace.

## Uninstall

If installed as an extension:

```bash
gemini extensions uninstall gemini-security-skills
```

If copied globally:

```bash
rm -rf ~/.gemini/skills/assembly-programming \
  ~/.gemini/skills/claude-mythos-emulation \
  ~/.gemini/skills/cybersecurity-partner \
  ~/.gemini/skills/devsecops \
  ~/.gemini/skills/exploit-development \
  ~/.gemini/skills/go-programming \
  ~/.gemini/skills/malware-reverse-engineering \
  ~/.gemini/skills/multilingual \
  ~/.gemini/skills/offensive-security \
  ~/.gemini/skills/prompt-enhancement \
  ~/.gemini/skills/python-programming \
  ~/.gemini/skills/soc-operations
```

