# Codex Workshop — Setup Guide

This fork of [Vendure](https://github.com/vendurehq/vendure) is the demo repo for the Codex Workshop. It packages five graduated lab examples on top of an unmodified Vendure codebase.

**Workshop branch:** `workshop/v1`

**Vendure base commit:** `3fc46f100c41d24ca39dad37fd8296b7d5509f8b` (forked from `vendurehq/vendure@master`)

---

## Lab examples

All five examples live under [`codex-labs/`](./codex-labs/).

| # | Directory | Time | What it covers |
|---|---|---|---|
| 01 | [`codex-labs/01-understand/`](./codex-labs/01-understand/README.md) | ~5 min | Code understanding across services |
| 02 | [`codex-labs/02-generate-tests/`](./codex-labs/02-generate-tests/README.md) | ~5 min | Test generation and critical review |
| 03 | [`codex-labs/03-agents-md/`](./codex-labs/03-agents-md/README.md) | ~5 min | Same prompt with and without an `AGENTS.md` file |
| 04 | [`codex-labs/04-multi-file-refactor/`](./codex-labs/04-multi-file-refactor/README.md) | ~5 min | Plan-first refactoring across files |
| 05 | [`codex-labs/05-plan-first-feature/`](./codex-labs/05-plan-first-feature/README.md) | ~5 min | Architecture and scaffold for a feature |

---

## Setup — required before the session

This is a hands-on workshop. Each attendee runs prompts on their own machine. Complete this setup *before* arriving — about 10 to 15 minutes including `npm install`. Open the room 15 min early if you need help.

```bash
# 1. Clone this repo on the workshop branch
git clone --branch workshop/v1 https://github.com/cnones-insurgence/codex-workshop-vendure.git
cd codex-workshop-vendure

# 2. Use Node 18+
nvm use 18    # or your preferred Node version manager

# 3. Install dependencies (this takes a few minutes)
npm install

# 4. Build @vendure/common and @vendure/core
#    Required before Vitest will run — TypeScript path aliases like
#    @vendure/common/lib/generated-types resolve to built output.
npm run build:core-common

# 5. Install Codex CLI if not already present
#    https://github.com/openai/codex
codex --version

# 6. Authenticate Codex CLI (first time only)
codex
```

Two extra side-terminal worktrees are used during the demo for the longer examples — those get created live during the session. You don't need to set them up ahead of time.

> **Note on `npm run build:core-common`:** without this build step, ~80% of the Vitest suite fails with `Cannot find package '@vendure/common/lib/generated-types'`. Always run it after `npm install` and after pulling new changes that touch `@vendure/common` or `@vendure/core`.

---

## During the session

Prompts are dropped in chat. Paste them into your terminal and hit enter. Outputs vary slightly run-to-run because the model is non-deterministic — that's expected. Look for the patterns described, not the exact text.

---

## What was changed from upstream Vendure

This workshop branch makes **only** these changes on top of `vendurehq/vendure@master`:

- Renamed root `AGENTS.md` → `AGENTS.upstream.md` (and its `CLAUDE.md` symlink → `CLAUDE.upstream.md`) so Example 03's "before" state has no AI-context file present.
- Added `AGENTS.md.example` at the root with Vendure-specific and organisation-specific coding standards used in Example 03.
- Added a `codex-labs/` directory with five example subdirectories (`01-understand/` through `05-plan-first-feature/`), each with its own README.
- Added this `WORKSHOP.md`.
- Prepended a short workshop banner to the existing `README.md`.

No source code under `packages/` has been modified.

---

## Reference: original Vendure README

The full upstream Vendure README is preserved at [`README.md`](./README.md) below the workshop banner.
