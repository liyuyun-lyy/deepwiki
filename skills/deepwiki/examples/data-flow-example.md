# Data Flow

## Primary Flows
- Index generation: scan repo -> build INDEX/TOC.

## Step-by-Step
1. Read `README.md` and build config files.
2. Identify modules and entry points.
3. Write `deepwiki/INDEX.md` and `deepwiki/TOC.md`.

## Inputs and Outputs
- Inputs: repo files, config.
- Outputs: markdown pages under `deepwiki/`.

## Diagrams
```mermaid
sequenceDiagram
  participant Repo
  participant Generator
  Repo->>Generator: Read sources
  Generator->>Repo: Write deepwiki pages
```

## State and Storage
- Output files only; no database.

## Source References
- src/generator/index.ts
