# Overview

## Purpose
- Generate and update deepwiki docs for a repository.
- Provide a predictable `/deepwiki` CLI workflow.

## Repo Layout
- `src/cli/` handles command parsing and execution.
- `src/generator/` builds markdown pages.

## Entry Points
- `src/cli/main.ts` wires `/deepwiki` commands.

## Where to Start
- Read `README.md` for install and usage.
- Run `/deepwiki:index` to build the initial index.

## How to Navigate
- Start with `deepwiki/INDEX.md`, then follow module links.

## Missing Image Reporting
- Missing image: `docs/architecture.md` → `assets/mermaid3.jpg` (blocked: path escapes repo root)

## Source References
- README.md
- src/cli/main.ts
