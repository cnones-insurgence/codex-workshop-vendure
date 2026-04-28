# Example 04 — Plan-First Refactoring

**Time:** ~5 min · **Surface:** Codex CLI

## What you'll see

We'll ask Codex to add a new state to the payment state machine — but crucially, we'll tell it to *plan* the change before writing any code. It comes back with a list of files to change, transitions to add or update, tests to change, and downstream risks.

This example runs in a side-terminal worktree (`codex-ws-ex04`) in the background while live work happens in the main terminal.

## Prompt

```
Add a 'PartiallyRefunded' state to the payment state machine. Note that
Vendure uses module augmentation (declare module) and custom PaymentProcess
definitions for extending payment states. Before making any changes, outline
your plan: what files need to change, what new transitions are needed, what
existing transitions need updating, what tests should change, and what could
break in downstream services.
```

## Verify (only if accepting the changes)

```bash
cd packages/core && npx tsc -p ./build/tsconfig.build.json --noEmit
```

## After the session

This example is about the single highest-leverage habit when working with AI coding tools: **plan first, code second.**

A bad plan caught here costs nothing — you read it, you push back, Codex revises. A bad plan caught in code review costs hours. A bad plan that ships costs days.

The plan should do four things:

1. **Identify all affected files**, including ones in adjacent modules a junior engineer might miss.
2. **Surface architectural insights** — like noticing that an existing flow doesn't currently transition some state it logically should.
3. **Push back on ambiguity** in the prompt rather than guessing the intended interpretation.
4. **List downstream breakage risks** so estimates and review effort are calibrated correctly.

When you adopt this habit on your own codebase, the prompt structure matters: ask for the plan explicitly, ask for the breakdown by category (files, transitions, tests, risks), and tell Codex *not to make changes yet*.
