# Research: Local Image Support

## Decision 1: Treat this repo as spec-only, with implementation in the CLI codebase

- **Decision**: The implementation plan targets the deepwiki CLI generator, while this repository retains only specs and skill assets.
- **Rationale**: The repository contains no application source code or test harnesses, so changes here are limited to specification and guidance artifacts.
- **Alternatives considered**: Bootstrap new application code within this repo. Rejected because it conflicts with the repo’s current purpose and lack of runtime scaffolding.

## Decision 2: Resolve image paths relative to project root with strict path safety

- **Decision**: Image references are treated as project-relative paths and are blocked if they escape the repository root.
- **Rationale**: This enforces FR-004 and prevents leaking or accessing files outside the project boundary.
- **Alternatives considered**: Allow absolute paths or parent-directory traversal. Rejected due to security and determinism risks.

## Decision 3: Copy image assets into output without modifying sources

- **Decision**: The generator includes image assets in output while keeping originals unchanged.
- **Rationale**: Meets FR-002 and FR-008, and supports deterministic outputs.
- **Alternatives considered**: Inline images as data URIs. Rejected due to potential size bloat and degraded page performance.

## Decision 4: Initial format scope

- **Decision**: Support common diagram formats (JPG, PNG) as an initial baseline.
- **Rationale**: Matches the assumption in the spec and covers the cited examples.
- **Alternatives considered**: Support all image formats immediately. Rejected due to unclear validation and compatibility expectations.

## Decision 5: Preserve mermaid blocks in Markdown

- **Decision**: Mermaid diagram blocks remain as mermaid code blocks in the generated Markdown.
- **Rationale**: Ensures Markdown renderers with Mermaid support can render diagrams without generating image files.
- **Alternatives considered**: Convert mermaid blocks into image assets. Rejected because the requirement is to keep Mermaid in Markdown.
