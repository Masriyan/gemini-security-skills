# Prompting and multilingual workflows

This document covers the communication-focused skills.

## Prompt enhancement workflow

Use `prompt-enhancement` when a request is vague, overloaded, or unreliable.

Recommended prompt:

```text
Use prompt-enhancement to rewrite this prompt for a coding agent. Preserve the
intent, add missing constraints, and include validation criteria.
```

The skill organizes prompts into:

- Objective.
- Context.
- Inputs.
- Process.
- Output.
- Validation.
- Boundaries.

Good enhanced prompts are:

- Specific enough to execute.
- Clear about files, commands, and constraints.
- Explicit about what not to change.
- Testable.
- Not overloaded with unnecessary persona text.

## Multilingual workflow

Use `multilingual` for translation, localization, terminology review, and
bilingual output.

Recommended prompt:

```text
Use multilingual to translate this technical documentation from English to
Indonesian. Preserve commands, code, product names, and URLs.
```

The skill should:

- Identify source and target language or locale.
- Preserve technical tokens.
- Adapt tone to the audience.
- Flag ambiguous terms.
- Keep terminology consistent.

Use locale-specific instructions when needed:

```text
Target locale: Indonesian for technical practitioners in Indonesia.
Tone: direct, professional, and concise.
Preserve: commands, file paths, hashes, URLs, and API names.
```

## Claude-like behavior workflow

Use `claude-mythos-emulation` to create an original behavior guide inspired by
observable Claude-like interaction patterns.

Recommended prompt:

```text
Use claude-mythos-emulation to create an assistant behavior spec that is
careful, direct, safety-aware, and collaborative. Do not claim to be Claude.
```

The skill should:

- Avoid identity claims.
- Avoid copying proprietary hidden prompts.
- Use careful reasoning and explicit uncertainty.
- Prefer structured, calm, practical answers.
- Include refusal and boundary behavior when relevant.

## Combined workflow examples

Use `prompt-enhancement` and `multilingual` together for localized prompts:

```text
Use prompt-enhancement to improve this SOC triage prompt, then use multilingual
to localize it into Indonesian while preserving SIEM field names.
```

Use `claude-mythos-emulation` and `prompt-enhancement` together for agent
specifications:

```text
Use claude-mythos-emulation to define the assistant style, then use
prompt-enhancement to convert it into a clean system prompt with tests.
```

