# Contributing

Contributions are welcome if they improve the quality, safety, clarity, or
coverage of Gemini Security Skills.

Repository URL:

```text
https://github.com/Masriyan/gemini-security-skills
```

## Contribution priorities

High-value contributions include:

- Clearer skill descriptions that improve activation accuracy.
- Better safety boundaries for dual-use security workflows.
- More precise workflows for realistic operational tasks.
- Documentation improvements.
- Validation fixes.
- New skills with a focused, reusable purpose.

Avoid contributions that:

- Add unauthorized offensive guidance.
- Add malware improvement or evasion guidance.
- Add vague persona text without operational value.
- Duplicate existing skill coverage.
- Add large generated files without a clear use.

## Repository layout

Extension skills live under:

```text
skills/<skill-name>/SKILL.md
```

Root-level skill folders are retained for direct copy workflows. When changing
a skill, keep the root-level copy and `skills/` copy synchronized unless the
repository later removes the duplicate layout.

## Skill authoring rules

Use these rules for `SKILL.md` files:

- Start with YAML frontmatter on line 1.
- Include `name:` and `description:`.
- Match folder name and `name:`.
- Use lowercase hyphenated names.
- Make the description specific because it controls activation.
- Keep the body concise and procedural.
- Include safety boundaries for dual-use work.
- Prefer workflows, checklists, and output formats over generic teaching text.

## Documentation rules

Use these rules for Markdown:

- Use clear headings.
- Use fenced code blocks with language tags when possible.
- Keep commands copyable.
- Use repository URL `https://github.com/Masriyan/gemini-security-skills`.
- Prefer relative links for local files.
- Keep security claims precise.

## Validation

Validate JSON:

```bash
python -m json.tool gemini-extension.json
```

Validate skills:

```bash
for d in skills/*/; do
  python /home/sudo3rs/.codex/skills/.system/skill-creator/scripts/quick_validate.py "${d%/}"
done
```

Check local Markdown links:

```bash
python - <<'PY'
from pathlib import Path
import re, sys
bad = []
for path in Path('.').rglob('*.md'):
    text = path.read_text(errors='ignore')
    for match in re.finditer(r'\[[^\]]+\]\(([^)]+)\)', text):
        target = match.group(1).split('#', 1)[0]
        if not target or '://' in target or target.startswith('mailto:'):
            continue
        if not (path.parent / target).exists():
            bad.append((path, target))
if bad:
    for path, target in bad:
        print(f'{path} -> {target}')
    sys.exit(1)
print('Markdown local links OK')
PY
```

Search for stale URLs and placeholders:

```bash
rg -n "TODO|\\[TODO|github.com" .
```

## Pull request checklist

Before submitting a change:

- Validate `gemini-extension.json`.
- Validate all changed skills.
- Check Markdown local links.
- Check that docs and README agree on installation commands.
- Confirm all GitHub repository links use
  `https://github.com/Masriyan/gemini-security-skills`.
- Confirm cyber security content stays within authorized, defensive,
  educational, or lab-scoped boundaries.

