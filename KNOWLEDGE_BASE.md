# Knowledge base

This knowledge base collects core concepts behind the skills in this
repository. It is not a replacement for the individual `SKILL.md` files. It is
background material for users and maintainers.

## Agent Skills model

An Agent Skill is a directory that contains `SKILL.md`. The file has YAML
frontmatter with `name:` and `description:` followed by Markdown instructions.

Gemini CLI uses the metadata for discovery and activation. The skill body is
loaded when the skill is activated.

Core principles:

- The `description:` field is the trigger surface.
- The body should contain procedural guidance, not generic filler.
- Bundled resources should live beside the skill when deterministic tools,
  templates, or references are needed.
- Skills should be narrow enough to activate predictably and broad enough to
  cover real user phrasing.

## Repository skill taxonomy

The skills are grouped into four knowledge areas:

- Secure engineering: `go-programming`, `python-programming`,
  `assembly-programming`, and `devsecops`.
- Offensive and vulnerability research: `offensive-security` and
  `exploit-development`.
- Defensive operations: `soc-operations`, `malware-reverse-engineering`, and
  `cybersecurity-partner`.
- Communication and agent behavior: `prompt-enhancement`, `multilingual`, and
  `claude-mythos-emulation`.

## Go programming knowledge

Important Go review areas:

- Package boundaries and exported API compatibility.
- `context.Context` propagation for request-scoped work.
- Error wrapping with `%w` when callers need to inspect causes.
- Goroutine lifecycle, cancellation, and channel close ownership.
- Race conditions around shared state and package globals.
- Table-driven tests and race tests for concurrency behavior.

Useful checks:

```bash
go test ./...
go test -race ./...
go test -run TestName ./path/to/package
go test -bench . ./path/to/package
```

## Python programming knowledge

Important Python review areas:

- Runtime version and dependency manager.
- Public boundary types and exception behavior.
- `pytest` fixtures, deterministic tests, and no hidden network dependency.
- Async flows that accidentally call blocking I/O.
- Unsafe deserialization, shell command construction, template injection, and
  broad exception handling.

Useful checks depend on project tooling:

```bash
pytest
ruff check .
mypy .
python -m compileall .
```

## Assembly programming knowledge

Important low-level analysis areas:

- Architecture, bitness, syntax, OS, ABI, compiler, and optimization level.
- Caller-saved and callee-saved registers.
- Stack alignment before calls.
- Flags and signed versus unsigned branches.
- Memory access width, sign extension, zero extension, and endian assumptions.
- Inline assembly constraints, clobbers, and `memory` effects.

Good assembly analysis translates code into pseudocode before recommending
changes.

## Offensive security knowledge

Authorized offensive security work starts with scope:

- Assets.
- Authorization owner.
- Test window.
- Allowed techniques.
- Exclusions.
- Rate limits.
- Data handling rules.
- Reporting requirements.

Assessment output should include evidence, impact, severity rationale,
reproduction summary, affected assets, remediation, and cleanup notes.

## Exploit development knowledge

Safe exploit-development work focuses on root cause and defensive validation.

Key concepts:

- Crash reproducibility.
- Target version, architecture, build flags, and mitigations.
- Input control and memory corruption class.
- Information disclosure and control-flow influence.
- Patch strategy and regression tests.

Avoid turning analysis into real-world weaponization.

## Malware reverse engineering knowledge

Safe malware analysis starts with isolation:

- Use snapshots.
- Disable shared clipboard.
- Avoid mounted personal directories.
- Control network access.
- Record hashes and provenance.

Common outputs:

- Behavior summary.
- Evidence.
- IOCs.
- Detection ideas.
- Containment, eradication, recovery, and monitoring steps.

## SOC operations knowledge

SOC triage depends on evidence quality.

Core questions:

- What triggered the alert?
- Which user, host, workload, or account is affected?
- Which timestamps and time zones apply?
- What events happened before and after the alert?
- Is this false positive, benign true positive, suspicious, confirmed incident,
  or insufficient data?
- What containment or monitoring action is justified by evidence?

## DevSecOps knowledge

DevSecOps connects security controls to the delivery path.

Commit-to-production review areas:

- Source control permissions.
- CI identity and token permissions.
- Third-party actions and dependency pinning.
- Secrets handling and OIDC federation.
- SAST, SCA, container, and IaC scanning.
- SBOM generation and artifact provenance.
- Deployment roles and environment separation.

## Prompt and multilingual knowledge

Good prompts specify:

- Objective.
- Context.
- Inputs.
- Process constraints.
- Output format.
- Validation criteria.
- Boundaries.

Good translation preserves:

- Meaning.
- Tone.
- Technical tokens.
- Commands.
- Code.
- URLs.
- Domain terminology.

