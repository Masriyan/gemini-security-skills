# Skill catalog

This catalog describes every skill in `https://github.com/Masriyan/gemini-security-skills`.
Use it to decide which skill should handle a task and what output quality to
expect.

## Programming skills

The programming skills focus on implementation, review, debugging, and
maintainability.

### `go-programming`

Use this skill for Go services, CLIs, APIs, modules, concurrency, tests, and
performance work.

Core knowledge:

- Go package structure, `go.mod`, `go.sum`, and module boundaries.
- Idiomatic interfaces, error wrapping, context propagation, and table-driven
  tests.
- Goroutine lifecycle, channel ownership, cancellation, race detection, and
  bounded concurrency.
- API compatibility and exported type review.
- Verification with `go test`, `go test -race`, benchmarks, and profiling.

Expected behavior:

- Inspect the package layout before editing.
- Prefer small, composable changes over large rewrites.
- Add tests for edge cases, failures, and concurrency behavior.

### `python-programming`

Use this skill for Python applications, CLIs, scripts, APIs, automation, data
processing, packaging, and tests.

Core knowledge:

- `pyproject.toml`, dependency managers, package layout, and entry points.
- Type hints, public boundary typing, `pytest`, fixtures, and deterministic
  tests.
- Async Python, blocking I/O risks, exception boundaries, and testable
  dependency injection.
- Secure handling of subprocesses, deserialization, templates, and untrusted
  input.

Expected behavior:

- Identify runtime and tooling before editing.
- Preserve behavior unless a change is requested.
- Run the existing formatter, type checker, and tests when available.

### `assembly-programming`

Use this skill for assembly snippets, disassembly, inline assembly, ABI issues,
crashes, reverse-engineering notes, and low-level performance.

Core knowledge:

- x86, x86-64, ARM, AArch64, and RISC-V reading patterns.
- Calling conventions, stack alignment, register preservation, flags, memory
  widths, and endian assumptions.
- Intel and AT&T syntax differences.
- Inline assembly constraints and compiler interaction.

Expected behavior:

- Identify architecture, ABI, syntax, OS, compiler, and optimization level.
- Translate assembly to pseudocode before recommending changes.
- Prioritize correctness and ABI compliance before optimization.

## Cyber security skills

The cyber security skills are scoped for authorized, defensive, educational, and
lab-based work.

### `offensive-security`

Use this skill for authorized penetration testing plans, web/API/cloud/mobile
assessment workflows, vulnerability validation, and reporting.

Core knowledge:

- Scope definition, authorization, exclusions, rate limits, test windows, and
  evidence handling.
- Reconnaissance and validation of owned or explicitly authorized assets.
- Safe proof practices that avoid unnecessary access expansion.
- Report writing with business impact, severity rationale, reproduction
  summaries, and remediation.

Expected behavior:

- Confirm authorization before active testing guidance.
- Avoid stealth, persistence, credential theft, destructive actions, and third
  party targeting.
- Pair findings with detection and remediation guidance.

### `exploit-development`

Use this skill for CTFs, lab targets, owned software, crash triage, fuzzing
results, exploitability assessment, and safe proof of concept design.

Core knowledge:

- Crash reproduction, target build flags, architecture, mitigations, and input
  vectors.
- Root-cause classes such as bounds errors, lifetime bugs, type confusion,
  races, parser bugs, and injection flaws.
- Exploitability concepts such as control flow influence, write primitives,
  information disclosure, sandboxing, and mitigations.
- Patch strategy, hardening, and regression tests.

Expected behavior:

- Keep proof of concept material minimal and lab-scoped.
- Prefer root cause, severity, remediation, and tests over weaponization.
- Avoid evasion, persistence, automated exploitation at scale, and
  post-exploitation.

### `malware-reverse-engineering`

Use this skill for suspicious binaries, scripts, documents, sandbox reports,
memory artifacts, indicators, and malware behavior summaries.

Core knowledge:

- Safe sample handling, isolated VMs, snapshots, and controlled networking.
- Static triage with hashes, strings, imports, sections, macros, scripts,
  packer hints, and config extraction.
- Dynamic analysis planning for process, filesystem, registry, and network
  behavior.
- IOC extraction, YARA/Sigma ideas, containment, eradication, and recovery.

Expected behavior:

- Treat samples as hostile.
- Focus on defensive triage, behavior, detection, and response.
- Avoid malware improvement, stealth, persistence, evasion, and deployment.

### `devsecops`

Use this skill for CI/CD hardening, IaC review, containers, Kubernetes, cloud
deployments, dependency security, release gates, SBOMs, and policy-as-code.

Core knowledge:

- Commit-to-production trust boundaries.
- Secrets, identities, build artifacts, provenance, and deployment permissions.
- SAST, SCA, container scanning, IaC scanning, signing, SBOM generation, and
  exception handling.
- Least privilege and release governance.

Expected behavior:

- Prefer incremental controls developers can keep using.
- Separate blocking release criteria from advisory findings.
- Verify controls with local checks, CI dry runs, or policy evaluation.

### `soc-operations`

Use this skill for alert triage, incident response, log analysis, detection
engineering, hunting, SIEM query planning, EDR investigation, and analyst notes.

Core knowledge:

- Evidence preservation, time zone handling, asset and user identity, and data
  source reliability.
- Timeline construction across process, network, authentication, file,
  registry, cloud, and identity events.
- Disposition decisions: false positive, benign true positive, suspicious,
  confirmed incident, or insufficient data.
- Escalation, containment, eradication, recovery, and monitoring.

Expected behavior:

- Separate facts from hypotheses.
- Produce analyst-ready summaries with evidence and gaps.
- Use MITRE ATT&CK when it improves clarity.

### `cybersecurity-partner`

Use this skill when you want a practical security collaborator for architecture
review, threat modeling, secure design, remediation planning, incident
readiness, or strategic decisions.

Core knowledge:

- Asset identification, actors, trust boundaries, controls, and abuse cases.
- Risk ranking by likelihood, impact, implementation cost, and constraints.
- Tactical and strategic security roadmaps.
- Review of code, configuration, architecture, and operational processes.

Expected behavior:

- Start from real constraints.
- Recommend concrete controls with owners and validation methods.
- Track residual risk and open questions.

## Communication and agent behavior skills

These skills improve how Gemini CLI communicates, reasons, and adapts output.

### `prompt-enhancement`

Use this skill for improving prompts, agent instructions, task specifications,
evaluation prompts, and output reliability.

Core knowledge:

- Objective, context, inputs, constraints, output format, validation, and
  boundaries.
- Ambiguity reduction and conflict detection.
- Reusable prompt templates and examples.

Expected behavior:

- Preserve user intent.
- Prefer testable instructions over personality-heavy wording.
- Add output structure only when it improves usability.

### `multilingual`

Use this skill for translation, localization, bilingual output, terminology
consistency, language detection, UI strings, documentation, and Indonesian to
English or English to Indonesian workflows.

Core knowledge:

- Locale-aware translation and tone matching.
- Preservation of code, commands, URLs, names, and security indicators.
- Terminology consistency and ambiguity handling.

Expected behavior:

- Ask for target locale when it materially changes the result.
- Prioritize natural target-language phrasing over literal translation.
- Flag uncertain idioms and high-stakes review needs.

### `claude-mythos-emulation`

Use this skill to create Claude-like assistant behavior specs, writing style,
reasoning discipline, refusal style, and prompt structures without claiming to
be Claude or copying proprietary hidden prompts.

Core knowledge:

- Observable style traits: careful reasoning, explicit uncertainty, calm tone,
  structured answers, and safety-aware collaboration.
- Behavior-spec design for agents, prompts, and UX.
- Anti-goals such as false identity claims and hidden prompt imitation.

Expected behavior:

- Produce original behavior instructions.
- Avoid identity claims and proprietary prompt copying.
- Include simple test prompts when validation is useful.

