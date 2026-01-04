# 🧭 deepwiki

Deepwiki skill and specification kit for generating repository documentation via Codex CLI and Claude Code.

## 📦 What this repo contains

- `skills/deepwiki/`: The deepwiki skill definition, templates, and examples.
- `specs/`: Feature specifications, plans, tasks, and checklists.
- `mermaid1.jpg`, `mermaid2.jpg`: Sample local images used in spec examples.

## 🤖 How to use (Claude Code)

This repo ships a Claude Code plugin manifest that points to the deepwiki skill.

- Add the marketplace: `/plugin marketplace add liyuyun-lyy/deepwiki`
- Install the plugin: `/plugin install deepwiki@deepwiki`
- Run the command: `/deepwiki`

## ✅ Supported clients

This repository supports both Codex CLI skills and Claude Code plugins.

## 🧰 How to use (Codex CLI)

Copy `skills/deepwiki` into your `~/.codex/skills/` directory, then use
`$deepwiki` to generate or update deepwiki content in a target repo. The model
detects whether this is the first run or an incremental update and proceeds
accordingly.

The skill writes all output under `deepwiki/` in the target repository.

The INDEX is generated dynamically based on repository structure and content.

## 🖼️ Image and Mermaid support

- Local images are referenced with project-relative paths and copied into `deepwiki/assets/`.
- Mermaid diagrams remain as Mermaid code blocks in Markdown so compatible renderers can render them inline.

## 🛠️ Development notes

- This repository focuses on skill behavior, templates, and specs, not the CLI implementation.
- Update the skill docs and examples whenever user-visible behavior changes.

## 📄 License

MIT. See `LICENSE`.
