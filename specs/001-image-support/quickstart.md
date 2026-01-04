# Quickstart: Local Image Support

## Goal

Verify that local image references (e.g., diagram JPG/PNG files) render in generated documentation and missing assets are reported.

## Prerequisites

- Documentation sources and local image files stored in the same repository
- Image references use project-relative paths

## Steps

1. Place image assets (for example, `mermaid1.jpg`, `mermaid2.jpg`) within the repo.
2. Add image references with alt text in the documentation source files.
3. Add a mermaid diagram block in a source page to validate Markdown rendering.
4. Run `/deepwiki:index` to collect repository inputs.
5. Run `/deepwiki:init` (or `/deepwiki:update` for an existing site) to generate docs.
6. Open the generated pages and confirm images and mermaid diagrams render inline.
7. Review the missing-asset report and fix any invalid paths.

## Expected Results

- All valid local image references appear in the generated pages.
- Alt text is preserved for accessibility.
- Missing or blocked images are reported with source page and path details.
