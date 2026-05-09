# FAQ

## What is this repository?

This repository is a Gemini CLI Agent Skills collection for security,
programming, reverse engineering, DevSecOps, SOC operations, prompt work, and
multilingual communication.

## What is the repository URL?

```text
https://github.com/Masriyan/gemini-security-skills
```

## What is the recommended install command?

```bash
gemini extensions install https://github.com/Masriyan/gemini-security-skills --consent
```

## Why are there root skill folders and a `skills/` folder?

The `skills/` folder is used by Gemini CLI extension installation. The
root-level folders are kept for direct copy compatibility and easier browsing.

## Which skills are included?

The repository includes:

- `go-programming`
- `python-programming`
- `assembly-programming`
- `offensive-security`
- `exploit-development`
- `malware-reverse-engineering`
- `devsecops`
- `soc-operations`
- `cybersecurity-partner`
- `prompt-enhancement`
- `multilingual`
- `claude-mythos-emulation`

## Are these skills safe for offensive security?

They are intended for authorized offensive security, defensive validation,
education, and lab work. They are not intended for unauthorized access,
stealth, persistence, credential theft, destructive activity, or malware
deployment.

## How do I verify the skills loaded?

Run this inside Gemini CLI:

```text
/skills list
```

If you installed or edited files while Gemini CLI was running, reload:

```text
/skills reload
```

## How do I update the extension?

```bash
gemini extensions update gemini-security-skills
```

## How do I use one skill directly?

Mention it by name:

```text
Use devsecops to review this CI/CD pipeline for secrets, permissions, and
artifact integrity.
```

## Can I use these skills outside Gemini CLI?

The skills use the `SKILL.md` format. Other compatible agent tools may be able
to read the same skill folders, but installation paths and activation behavior
depend on the tool.

