# Changelog

All notable changes to Gemini Security Skills are documented here.

## 1.0.0 - 2026-05-09

Initial repository release.

Added:

- Created 12 Agent Skills for Gemini CLI:
  `go-programming`, `python-programming`, `assembly-programming`,
  `offensive-security`, `exploit-development`,
  `malware-reverse-engineering`, `devsecops`, `soc-operations`,
  `cybersecurity-partner`, `prompt-enhancement`, `multilingual`, and
  `claude-mythos-emulation`.
- Added `gemini-extension.json` for Gemini CLI extension installation.
- Added top-level `skills/` directory for extension-bundled Agent Skills.
- Added root-level skill folders for direct copy compatibility.
- Added repository banner at `assets/banner.svg`.
- Added install, usage, catalog, workflow, safety, troubleshooting, and
  maintenance documentation.

Security posture:

- Cyber security skills are scoped to authorized, defensive, educational, and
  lab-based use.
- Offensive and exploit-development skills include explicit guardrails against
  unauthorized access, stealth, persistence, credential theft, destructive
  actions, malware improvement, and weaponization.

Validation:

- Validated all root-level skills.
- Validated all extension-bundled skills under `skills/`.
- Validated `gemini-extension.json` as JSON.
- Checked local Markdown links.

