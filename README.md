# deepwiki-kit

Deepwiki skill and specification kit for generating repository documentation via Codex CLI.

## What this repo contains

- `skills/deepwiki/`: The deepwiki skill definition, templates, and examples.
- `specs/`: Feature specifications, plans, tasks, and checklists.
- `mermaid1.jpg`, `mermaid2.jpg`: Sample local images used in spec examples.

## How to use (Codex CLI)

Use `$deepwiki` to generate or update deepwiki content in a target repo. The
model detects whether this is the first run or an incremental update and
proceeds accordingly.

The skill writes all output under `deepwiki/` in the target repository.

The INDEX is generated dynamically based on repository structure and content.

## How to use (Claude Code)

This repo ships a Claude Code plugin manifest that points to the deepwiki skill.

- Add the plugin: `/plugin add .` (or `/plugin add liyuyun-lyy/deepwiki`).
- Run the command: `/deepwiki`

## Image and Mermaid support

- Local images are referenced with project-relative paths and copied into `deepwiki/assets/`.
- Mermaid diagrams remain as Mermaid code blocks in Markdown so compatible renderers can render them inline.

## Development notes

- This repository focuses on skill behavior, templates, and specs, not the CLI implementation.
- Update the skill docs and examples whenever user-visible behavior changes.

## License

MIT. See `LICENSE`.
