# Comparison

This document compares the skills in this repository and explains when to use
each one.

## Quick selection table

| Need | Use |
| --- | --- |
| Write or review Go code | `go-programming` |
| Write or review Python code | `python-programming` |
| Analyze assembly or ABI behavior | `assembly-programming` |
| Plan authorized security testing | `offensive-security` |
| Analyze a lab crash or vulnerability | `exploit-development` |
| Triage suspicious malware artifacts | `malware-reverse-engineering` |
| Harden CI/CD or deployment flow | `devsecops` |
| Triage alerts and incidents | `soc-operations` |
| Threat model or security review a system | `cybersecurity-partner` |
| Improve a prompt or agent instruction | `prompt-enhancement` |
| Translate or localize content | `multilingual` |
| Create Claude-like behavior instructions | `claude-mythos-emulation` |

## Offensive security vs exploit development

Use `offensive-security` when the target is an authorized assessment and the
work is about planning, validation, evidence, and reporting.

Use `exploit-development` when the target is a lab, CTF, owned software, crash,
fuzzing result, or vulnerability root-cause task.

Main difference:

- `offensive-security` is assessment workflow oriented.
- `exploit-development` is vulnerability mechanics and safe proof oriented.

Both avoid unauthorized access, stealth, persistence, destructive actions, and
weaponization.

## SOC operations vs malware reverse engineering

Use `soc-operations` when the input is alert data, logs, timelines, SIEM
queries, EDR events, identity events, or incident response context.

Use `malware-reverse-engineering` when the input is a suspicious artifact,
binary, script, document, sandbox report, memory artifact, or behavior report.

Main difference:

- `soc-operations` decides what happened and what the response team should do.
- `malware-reverse-engineering` explains what an artifact does and how to detect
  or contain it.

## DevSecOps vs cybersecurity partner

Use `devsecops` when the work is tied to pipelines, infrastructure as code,
containers, Kubernetes, cloud deployment, release gates, secrets, SBOMs, or
policy-as-code.

Use `cybersecurity-partner` when the work is broader: architecture review,
threat modeling, risk prioritization, secure design, incident readiness, or
security roadmap planning.

Main difference:

- `devsecops` converts security requirements into build and deployment
  controls.
- `cybersecurity-partner` helps decide which risks and controls matter most.

## Prompt enhancement vs Claude mythos emulation

Use `prompt-enhancement` when you need a clearer, more reliable prompt for a
specific task.

Use `claude-mythos-emulation` when you need an assistant behavior specification
in a Claude-like style without identity claims or proprietary prompt copying.

Main difference:

- `prompt-enhancement` optimizes task execution.
- `claude-mythos-emulation` designs assistant behavior and tone.

## Programming skills vs security skills

Use programming skills when the main artifact is code correctness,
maintainability, tests, or runtime behavior.

Use security skills when the main artifact is a threat model, assessment,
incident note, vulnerability analysis, detection, or hardening plan.

For secure code work, combine them:

```text
Use python-programming to patch this parser, then use cybersecurity-partner to
review the security impact and residual risk.
```

