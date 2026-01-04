# deepwiki-kit

Deepwiki skill and specification kit for generating repository documentation via Codex CLI.

## What this repo contains

- `skills/deepwiki/`: The deepwiki skill definition, templates, and examples.
- `specs/`: Feature specifications, plans, tasks, and checklists.
- `mermaid1.jpg`, `mermaid2.jpg`: Sample local images used in spec examples.

## How to use (Codex CLI)

Use these commands to generate or update deepwiki content in a target repo:

- `/deepwiki`: Full run (init if missing, then update pages and index)
- `/deepwiki:init`: Create base structure and starter pages
- `/deepwiki:index`: Regenerate `deepwiki/INDEX.md` and `deepwiki/TOC.md`
- `/deepwiki:update`: Update existing pages without deleting user sections

The skill writes all output under `deepwiki/` in the target repository.

## Image and Mermaid support

- Local images are referenced with project-relative paths and copied into `deepwiki/assets/`.
- Mermaid diagrams remain as Mermaid code blocks in Markdown so compatible renderers can render them inline.

## Development notes

- This repository focuses on skill behavior, templates, and specs, not the CLI implementation.
- Update the skill docs and examples whenever user-visible behavior changes.
