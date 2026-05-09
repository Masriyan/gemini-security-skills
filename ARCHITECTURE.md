# Architecture

This repository is structured to support both Gemini CLI extension installation
and direct `SKILL.md` copy workflows.

## Main components

The primary components are:

- `gemini-extension.json`: Gemini CLI extension manifest.
- `skills/`: Extension-bundled Agent Skills.
- Root-level skill folders: Direct copy compatibility and easy browsing.
- `docs/`: Detailed documentation.
- `assets/banner.svg`: README banner.

## Extension layout

Gemini CLI extensions can bundle Agent Skills in a top-level `skills/`
directory.

```text
gemini-security-skills/
├── gemini-extension.json
└── skills/
    └── go-programming/
        └── SKILL.md
```

The extension install command is:

```bash
gemini extensions install https://github.com/Masriyan/gemini-security-skills --consent
```

## Skill layout

Each skill is self-contained:

```text
skill-name/
├── SKILL.md
└── agents/
    └── openai.yaml
```

`SKILL.md` is the required file. `agents/openai.yaml` is metadata for compatible
agent interfaces.

## Duplication policy

The same skills currently exist in two places:

- `skills/<skill-name>/`
- `<skill-name>/`

The `skills/` copy is the canonical extension install copy. The root-level copy
exists for direct installation compatibility and browsing. Maintainers should
keep both copies synchronized until the repository chooses one canonical layout
only.

## Safety architecture

Cyber security skills include boundaries in both metadata and body text. This
matters because the metadata influences activation before the full body is
loaded.

Safety requirements:

- Mention authorization and defensive purpose in dual-use skill descriptions.
- Put high-risk disallowed behavior in the skill body.
- Prefer remediation, detection, evidence, and containment outputs.
- Avoid operational misuse guidance.

