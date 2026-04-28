# Example 03 — `AGENTS.md` Before / After

**Time:** ~5 min · **Surface:** Codex CLI

## What you'll see

The same prompt run twice. The first time, no `AGENTS.md` file exists at the repo root — Codex builds a plugin using whatever it can infer from the rest of the codebase. The second time, an `AGENTS.md` file is in place — Codex reads it and applies the rules in there.

The `AGENTS.md.example` at the repo root contains both Vendure-specific patterns and organisation-specific rules (JSDoc tags, error message style, mandatory plugin README structure, mandatory subscriber tests, snake_case columns).

## Prompt

```
Create a new plugin called audit-log that subscribes to OrderPlacedEvent
and PaymentStateTransitionEvent and records them. Put it under
packages/audit-log-plugin/.
```

## Step 2 — activate the AGENTS.md

Between the two runs:

```bash
rm -rf packages/audit-log-plugin
mv AGENTS.md.example AGENTS.md
```

For the second run, the facilitator may bump reasoning effort to `medium` because the prompt now requires Codex to apply many constraints at once.

## Reset between rehearsals

```bash
rm -rf packages/audit-log-plugin
mv AGENTS.md AGENTS.md.example
```

## After the session

This example is about context injection — telling Codex *how this codebase does things* rather than letting it guess. An `AGENTS.md` file at the repo root is persistent: every prompt your engineers run from that point on follows whatever rules are written in it.

The Vendure-specific rules in `AGENTS.md` (use ErrorResult, use Vitest, no class-validator) make less difference than you might expect, because Codex can infer those from neighbouring code. The bigger difference comes from the *organisation-specific* rules — the things that aren't visible anywhere in the code (Jira ticket conventions in JSDoc, sentence-case error messages, mandatory README structure, mandatory tests for event subscribers).

This is why every team that adopts Codex (or any agentic coding tool) ends up writing its own `AGENTS.md`. It's the cheapest, highest-leverage adoption investment available — about 15 minutes of writing for persistent policy enforcement on every change going forward.
