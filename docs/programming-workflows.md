# Programming workflows

This document explains how to apply the programming skills for day-to-day
engineering work.

## Go workflow

Use `go-programming` for Go code changes, reviews, and debugging.

Recommended prompt:

```text
Use go-programming to review this Go package for correctness, race conditions,
API compatibility, and missing tests.
```

The skill should:

- Inspect `go.mod`, package layout, and tests.
- Identify public API boundaries.
- Review goroutine ownership and channel closing rules.
- Prefer clear errors and context-aware cancellation.
- Add table-driven tests.
- Run `go test ./...` or targeted package tests when practical.

High-risk Go areas:

- Goroutine leaks.
- Shared mutable state without synchronization.
- Nil interface confusion.
- Error wrapping that hides actionable causes.
- Context ignored in request-scoped work.
- Package globals that make tests flaky.

## Python workflow

Use `python-programming` for Python features, scripts, APIs, packaging, and
maintenance.

Recommended prompt:

```text
Use python-programming to implement this feature with tests and preserve the
existing public behavior.
```

The skill should:

- Detect Python version and dependency manager.
- Read `pyproject.toml`, requirements files, package layout, and tests.
- Keep changes targeted.
- Use typed public boundaries where the project already uses typing.
- Add deterministic tests with `pytest` or the existing framework.
- Avoid hidden network calls in tests.

High-risk Python areas:

- Unsafe deserialization.
- Shell command construction.
- Template injection.
- Mutable default arguments.
- Blocking I/O in async flows.
- Broad exception handling that hides failures.

## Assembly workflow

Use `assembly-programming` for low-level routines, disassembly, crash analysis,
and ABI review.

Recommended prompt:

```text
Use assembly-programming to explain this routine, map registers and stack
layout, and identify ABI or memory safety risks.
```

The skill should:

- Identify architecture, bitness, syntax, ABI, OS, and compiler.
- Track inputs, outputs, preserved registers, flags, and memory accesses.
- Translate assembly into pseudocode.
- Check stack alignment at calls.
- Check signed and unsigned branch semantics.
- Review inline assembly constraints and clobbers.

High-risk assembly areas:

- Incorrect stack alignment.
- Missing callee-saved register restoration.
- Wrong operand width.
- Sign extension bugs.
- Misread condition flags.
- Inline assembly without `memory` or register clobbers.

## Combining programming and security skills

Many engineering tasks benefit from combining skills.

Examples:

```text
Use go-programming to fix this handler, then use cybersecurity-partner to
review the security impact of the change.
```

```text
Use python-programming to refactor this parser, then use devsecops to add a CI
test that blocks unsafe parser regressions.
```

```text
Use assembly-programming and exploit-development to analyze this lab crash and
recommend a defensive patch.
```

