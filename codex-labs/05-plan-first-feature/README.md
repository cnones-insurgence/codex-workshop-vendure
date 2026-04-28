# Example 05 — Design & Implement a Feature

**Time:** ~5 min · **Surface:** Codex CLI

## What you'll see

We'll ask Codex to design and scaffold a brand new plugin from scratch — a loyalty-points feature. Architecture first (entities, services, events), then the actual scaffold files. This is the closest the demo gets to what real feature work with Codex looks like.

This example runs in a side-terminal worktree (`codex-ws-ex05`) in the background while live work happens in the main terminal.

## Prompt

```
Design a loyalty-points plugin for this ecommerce platform. First, outline
the architecture: what entities, services, and events are needed. Then
implement the core plugin scaffold following the existing plugin patterns
in this codebase.
```

## After the session

This example is about how AI coding tools actually fit into real feature work. The pattern that matters:

1. **Architecture before code.** Get the entities, services, and event flow on screen before any file is written. Review the design as if it were a colleague's RFC.
2. **Reuse existing patterns.** Codex should be composing the patterns your codebase already uses (plugin scaffolding, entity conventions, event subscribers), not inventing new framework choices on the side.
3. **Watch for engineering judgment calls.** Look for moments where Codex makes a deliberate trade-off and explains it — *"backend-first for now, easy to extend with a GraphQL surface later"*, *"separate account from transaction so changes are auditable"*. These are the bits that distinguish useful AI output from impressive-looking AI output.
4. **Pay attention to what Codex says it didn't do.** *"The scaffold intentionally stops short of a migration"* — that kind of honest scope note is what makes Codex output reviewable. The gaps are as important as the code.

This is the example most engineers will eventually use Codex for. The pattern (architecture review → scaffold → migration → fill in logic → tests) becomes natural with practice.
