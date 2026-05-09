# Cybersecurity workflows

This document provides practical workflows for the cyber security skills in
this repository.

## Authorized assessment workflow

Use `offensive-security` for ethical assessment planning and validation.

Recommended prompt:

```text
Use offensive-security to plan an authorized assessment for these assets:
<assets>. Scope: <scope>. Exclusions: <exclusions>. Test window: <time>.
Allowed techniques: <techniques>. Reporting format: <format>.
```

Expected phases:

1. Confirm authorization and scope.
2. Identify asset type and test strategy.
3. Select safe checks and rate limits.
4. Collect evidence with minimal impact.
5. Validate risk without unnecessary access expansion.
6. Report impact, severity, reproduction summary, and remediation.

## Vulnerability research workflow

Use `exploit-development` for lab-safe vulnerability analysis.

Recommended prompt:

```text
Use exploit-development to analyze this crash in my lab target. Architecture:
<arch>. Build flags: <flags>. Mitigations: <mitigations>. Crash log:
<log>.
```

Expected phases:

1. Reproduce the crash in an isolated environment.
2. Identify root cause and affected code path.
3. Classify exploitability at a defensive level.
4. Produce a minimal safe proof if needed.
5. Recommend patch, hardening, and regression tests.

## Malware triage workflow

Use `malware-reverse-engineering` for suspicious files, scripts, and sandbox
reports.

Recommended prompt:

```text
Use malware-reverse-engineering to triage this suspicious artifact report.
Include summary, evidence, IOCs, detection ideas, and response actions.
```

Expected phases:

1. Record metadata such as filename, hash, size, type, source, and timestamp.
2. Review static indicators such as strings, imports, sections, macros, and
   script behavior.
3. Plan or summarize dynamic behavior safely.
4. Classify capabilities such as execution, persistence, discovery, C2,
   collection, and exfiltration.
5. Produce IOCs and defensive response steps.

## SOC alert triage workflow

Use `soc-operations` for alert investigation and incident notes.

Recommended prompt:

```text
Use soc-operations to triage this alert. Include disposition, evidence, scope,
actions, and gaps. Logs: <logs>.
```

Expected phases:

1. Summarize the alert source, time, user, host, rule, and severity.
2. Validate data quality and enrichment.
3. Build a timeline.
4. Determine disposition.
5. Recommend containment, eradication, recovery, and monitoring.

## DevSecOps hardening workflow

Use `devsecops` for pipelines, IaC, containers, Kubernetes, cloud, and release
controls.

Recommended prompt:

```text
Use devsecops to review this pipeline and deployment flow. Focus on secrets,
permissions, dependency risk, artifact integrity, and release gates.
```

Expected phases:

1. Map commit-to-production flow.
2. Identify trust boundaries and identities.
3. Review secrets and artifact handling.
4. Add or tune scanning and policy gates.
5. Recommend SBOM, signing, provenance, and least privilege controls.

## Security partner workflow

Use `cybersecurity-partner` when you need broader security collaboration.

Recommended prompt:

```text
Use cybersecurity-partner to threat model this architecture and prioritize the
top risks by likelihood, impact, and implementation effort.
```

Expected outputs:

- Assets and trust boundaries.
- Threat actors and abuse cases.
- Existing controls.
- Ranked risks.
- Tactical mitigations.
- Strategic roadmap.
- Residual risk and open questions.

