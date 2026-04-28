# Example 02 — Generate Tests

**Time:** ~5 min · **Surface:** Codex CLI

## What you'll see

We'll ask Codex to write unit tests for a non-trivial piece of pricing logic — the order calculator that handles tax-inclusive prices, multi-line promotions, and partial allocation when stock runs out mid-cart. Codex follows the existing test patterns in the repo.

## Prompt

```
Write unit tests for OrderCalculator.applyPriceAdjustments covering the
interaction between tax-inclusive prices, multi-line promotion conditions,
and partial allocation when stock runs out mid-cart. Follow the existing
test patterns in this repo.
```

## Verify

```bash
cd packages/core && npx vitest run order-calculator
```

## After the session

This example is about reading AI-generated tests like a senior reviewer. The hard part isn't getting Codex to *write* tests — it does that fine. The hard part is asking, after the tests pass, *what are they actually checking?*

A test that asserts the discount has the right *name* is not the same as a test that asserts the discount has the right *amount*. A test that interprets "stock running out" as "manually changed quantity" is technically valid but doesn't test what was asked for. Tests that pass on the first run feel safer than tests that fail — and that feeling is the trap.

The skill engineers need to develop here isn't prompt engineering. It's the discipline of reading AI-generated tests with the same scepticism they'd apply to a junior engineer's first PR.
