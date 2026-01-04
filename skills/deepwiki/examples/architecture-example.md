# Architecture

## System Context
- Local CLI reads repo files and writes deepwiki pages.

## Components
- CLI command runner: parses `/deepwiki` actions.
- Generator: produces markdown from scanned sources.

## Key Flows
- Index build: scan repo -> write INDEX/TOC.

## Diagrams
```mermaid
flowchart LR
  Repo[Repository] --> Scan[Scan Sources]
  Scan --> Pages[Generate Pages]
```

## Interfaces and Contracts
- Markdown output in `deepwiki/` with fixed filenames.

## Runtime and Deployment
- Runs locally as a Codex CLI skill.

## Source References
- src/cli/main.ts
- src/generator/index.ts
