# Security boundaries

This repository includes dual-use cyber security skills. The skills are written
to support authorized work, defensive outcomes, education, and controlled lab
research.

## Allowed work

The cyber security skills are appropriate for:

- Assets you own.
- Systems you are explicitly authorized to test.
- Internal defensive operations.
- CTFs and intentionally vulnerable labs.
- Malware triage in isolated analysis environments.
- Secure design, remediation, and risk reduction.
- Detection engineering and incident response.

## Disallowed work

The skills should not be used for:

- Unauthorized access to third-party systems.
- Credential theft, phishing, or account takeover.
- Persistence, stealth, evasion, or bypassing monitoring.
- Destructive actions or data theft.
- Malware improvement, deployment, or operationalization.
- Exploit weaponization against real targets.
- Automated exploitation at scale.

## Safe proof standard

When validating a vulnerability, use the minimum proof required to establish
risk:

- Demonstrate the issue in a lab or explicitly authorized environment.
- Avoid expanding access beyond the agreed scope.
- Avoid collecting sensitive data.
- Capture timestamps, inputs, outputs, and affected versions.
- Clean up test artifacts.
- Provide detection and remediation guidance with the finding.

## Offensive security guardrails

The `offensive-security` skill requires scope before active testing guidance.
Good scope includes:

- Target assets and exclusions.
- Authorization owner.
- Allowed techniques.
- Test window.
- Rate limits.
- Data handling rules.
- Reporting requirements.

If scope is missing, the agent should ask for it or provide only high-level,
non-operational planning guidance.

## Exploit development guardrails

The `exploit-development` skill is for labs, CTFs, owned software, and
defensive validation.

Safe output focuses on:

- Root cause.
- Reproduction constraints.
- Exploitability classification.
- Mitigations and hardening.
- Regression tests and fuzzing strategy.

Unsafe output includes:

- Persistence.
- Evasion.
- Post-exploitation.
- Credential collection.
- Turnkey real-world exploitation.
- Automated scanning or exploitation of public targets.

## Malware reverse engineering guardrails

The `malware-reverse-engineering` skill treats every sample as hostile.

Safe analysis uses:

- Isolated VMs.
- Snapshots.
- No shared clipboard.
- No mounted personal directories.
- Controlled networking.
- Hashing, static triage, and monitored dynamic analysis.

The skill should produce:

- Behavior summaries.
- Evidence.
- Indicators of compromise.
- Detection ideas.
- Containment, eradication, recovery, and monitoring steps.

It should not produce malware improvement, stealth, persistence, evasion, or
deployment guidance.

## SOC and DevSecOps guardrails

The `soc-operations` and `devsecops` skills are defensive by design.

SOC outputs should distinguish facts from hypotheses, preserve evidence, and
avoid over-scoping incidents without proof.

DevSecOps outputs should reduce practical risk without creating unusable
release gates. Controls should be specific, testable, and maintainable.

