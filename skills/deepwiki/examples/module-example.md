# Module: Generator

## Responsibilities
- Build markdown pages from scanned sources.

## Key Files
- `src/generator/index.ts`: entry for generation pipeline.

## Public Interfaces
- `generateIndex()`, `generatePages()`.

## Diagrams
```mermaid
flowchart TB
  CLI[CLI] --> Generator
  Generator --> Pages[Pages]
```

## Configuration
- `deepwiki.config.json`.

## Tests
- `tests/generator/`.

## Source References
- src/generator/index.ts
