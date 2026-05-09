# Usage

This guide shows how to use Gemini Security Skills after installation.

## List loaded skills

Inside Gemini CLI, run:

```text
/skills list
```

Reload after edits or installation:

```text
/skills reload
```

Disable or enable a skill when you need tighter control:

```text
/skills disable offensive-security
/skills enable offensive-security
```

## Invoke a skill explicitly

Explicit invocation is the most predictable way to use a skill.

```text
Use go-programming to review this package for race conditions and missing tests.
```

```text
Use soc-operations to triage this alert and produce an analyst-ready summary.
```

```text
Use prompt-enhancement to rewrite this task for a coding agent.
```

## Invoke a skill naturally

Gemini CLI can activate a skill when the task matches the skill description.

Examples:

- "Review this Go API for goroutine leaks."
- "Triage these EDR events and decide whether this is an incident."
- "Translate this README into Indonesian while preserving commands."
- "Threat model this architecture and rank the top risks."

## Combine skills

For multi-step work, specify the order.

```text
Use cybersecurity-partner to threat model this design, then use devsecops to
turn the top risks into CI/CD controls.
```

```text
Use malware-reverse-engineering to summarize this sandbox report, then use
soc-operations to create a hunting plan.
```

```text
Use prompt-enhancement to clarify this lab prompt, then use
exploit-development to analyze the crash safely.
```

## Good prompt pattern

Use this pattern for best results:

```text
Use <skill-name> for <task>.
Context: <system, files, logs, target, or constraints>.
Goal: <decision, patch, report, plan, or explanation required>.
Boundaries: <what not to do, scope limits, safety limits>.
Output: <format, sections, length, or artifact required>.
Validation: <tests, checks, or evidence needed>.
```

## Cyber security usage rules

For cyber security tasks, include authorization and scope.

Good:

```text
Use offensive-security to plan an authorized assessment for my lab API at
https://lab.example.local. Scope is staging only. No destructive tests. Rate
limit to 2 requests per second. Output a test plan and report template.
```

Bad:

```text
Hack this random website and show me how to stay hidden.
```

The skills are designed for authorized testing, defensive operations,
education, and lab work. They are not designed for unauthorized access,
stealth, persistence, credential theft, destructive activity, or malware
deployment.

## Programming usage examples

Go:

```text
Use go-programming to implement request cancellation in this service and add
tests for timeout and client disconnect behavior.
```

Python:

```text
Use python-programming to refactor this parser, add pytest coverage, and check
for unsafe deserialization risks.
```

Assembly:

```text
Use assembly-programming to explain this x86-64 function, map register usage,
and identify ABI violations.
```

## Defensive operations examples

SOC:

```text
Use soc-operations to triage these authentication logs. Return disposition,
timeline, impacted accounts, recommended actions, and telemetry gaps.
```

Malware reverse engineering:

```text
Use malware-reverse-engineering to analyze this sandbox report. Return summary,
evidence, IOCs, detection ideas, and response actions.
```

DevSecOps:

```text
Use devsecops to harden this GitHub Actions workflow. Focus on permissions,
secret exposure, dependency pinning, SBOM, and artifact integrity.
```

