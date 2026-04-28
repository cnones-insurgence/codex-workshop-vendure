# Example 01 — Understand Unfamiliar Code

**Time:** ~5 min · **Surface:** Codex CLI

## What you'll see

We'll ask Codex to explain the checkout flow in this codebase — from cart creation through to payment confirmation. It's a comprehension task: Codex reads files and tells us what's there.

## Prompt

```
Explain the checkout and order lifecycle in this codebase. Start from the
main order service and trace the flow from cart creation through to payment
confirmation. What services does it depend on? What state transitions are
valid? Where does payment fit in?
```

## Verify

This is a read-only example. No commands to run after.

## After the session

This example shows the cheapest, highest-trust use case for a coding agent: helping engineers onboard into an unfamiliar codebase on day one.

The thing that makes Codex output verifiable — versus a chatbot that sounds like it knows your code — is the file and line numbers next to every claim. If you can click through to the actual source, you can trust it. If you can't, you're guessing.

This is also the example where reasoning effort matters least: the work is mostly file traversal, not deep design. Use the cheapest reasoning level you have.
