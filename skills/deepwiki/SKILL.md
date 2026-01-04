---
name: deepwiki
description: Generate or update a repository understanding deepwiki as Markdown, including a dynamic INDEX.md under deepwiki/. Use when users ask for /deepwiki, /deepwiki:init, /deepwiki:index, /deepwiki:update, or request a repo deepwiki/knowledge base.
---

# Deepwiki Generator

Create a Markdown-based deepwiki for a code repository. Always write files under `deepwiki/`.

## Language selection

Before generating any deepwiki content, ask the user to choose the output language
as a multiple-choice prompt:

A) English
B) Chinese
C) Other (please specify)

If the user does not specify a language, default to English and note it explicitly.

## Commands and intent

- `/deepwiki` or "generate deepwiki": run the full flow; the model detects whether this is the first run or an update and proceeds accordingly.

## Output structure (fixed)

Always ensure these exist:

- `deepwiki/INDEX.md` - landing page summary and entry links.
- `deepwiki/assets/` - local images and rendered diagram assets.

Recommended pages (create as needed):

- `deepwiki/overview.md`
- `deepwiki/architecture.md`
- `deepwiki/modules/<module>.md`
- `deepwiki/dependencies.md`
- `deepwiki/data-flow.md`
- `deepwiki/glossary.md`

## Image and diagram support

- Render local images inline using project-relative paths and keep them under
  `deepwiki/assets/` in the generated output.
- Preserve mermaid diagram blocks in Markdown so compatible renderers can
  render them inline.
- Always include at least one mermaid diagram in pages that have a Diagrams
  section; if none is obvious, add a simple placeholder diagram and mark it
  with a TODO for refinement.
- Use deterministic filenames for copied local images (consistent for the same
  source page and reference order).
- Preserve alt text or captions from the source content.
- If an image or diagram cannot be resolved, emit a missing-asset note that
  includes the source page and the referenced path.

## Templates and examples

Use the templates in `templates/` for page structure and the samples in
`examples/` for tone and formatting. Templates define required sections and
minimum content expectations.

Templates:
- `templates/overview.md`
- `templates/architecture.md`
- `templates/dependencies.md`
- `templates/data-flow.md`
- `templates/module.md`
- `templates/glossary.md`

Examples:
- `examples/overview-example.md`
- `examples/architecture-example.md`
- `examples/dependencies-example.md`
- `examples/data-flow-example.md`
- `examples/module-example.md`
- `examples/glossary-example.md`

## Workflow

0) Confirm output language:
   - Present choices: A) English, B) Chinese, C) Other (please specify).
   - If not specified, default to English and proceed.

1) Scan the repo:
   - Identify primary languages, entry points, build tools, and key directories.
   - Capture module boundaries (top-level packages, services, libs).
   - Note key files: README, build config, main entrypoints, API specs, etc.

2) Draft content:
   - Keep it concise, factual, and link to code locations.
   - Prefer short sections with bullet points over long prose.
   - Include "How to navigate" and "Where to start" guidance.

3) Write or update pages:
   - On first run, create the recommended pages with placeholders.
   - On subsequent runs, preserve existing headings and add deltas.

4) Render images and diagrams:
   - Copy local images referenced by content into `deepwiki/assets/`.
   - Preserve mermaid diagram blocks in Markdown.
   - Insert image references inline with alt text.

5) Regenerate index and toc:
5) Regenerate index:
   - `INDEX.md` should summarize the repo and link to all core pages.
   - Group entries dynamically based on repo structure and content.

## Page layout requirements

Each page MUST follow its template structure and include a "Source References"
section listing the relevant paths.

**Update Notes format** (use when modifying existing pages):

```
## Update Notes
- YYYY-MM-DD: Short summary of what changed and why.
```

## Minimum content checklist

- Overview: purpose, repo layout, entry points, and navigation guidance.
- Architecture: components, key flows, and interfaces/contracts.
- Dependencies: build/runtime deps, external services, and dev tools.
- Data Flow: primary flows with inputs/outputs and storage/state.
- Modules: responsibilities, key files, public interfaces, and tests.
- Glossary: key terms used across docs or code.
- Diagrams: include at least one mermaid diagram when a Diagrams section exists.

## Source citation rules

- Use "Source References" at the end of each page.
- List paths as bullet points, e.g., `- src/app/main.ts`.
- If a claim lacks evidence, add a TODO note in the section.

## Dynamic INDEX rules

- Sections are derived from detected repository structure and deepwiki pages.
- Omit empty sections; never include placeholders with no entries.
- Use deterministic ordering for sections and entries across runs.
- Ensure every generated deepwiki page appears in the INDEX.

## Index template (example when applicable)

Use this structure for `deepwiki/INDEX.md`:

```
# Deepwiki Index

## Summary
- Purpose:
- Tech stack:
- Entry points:
- Where to start:
- How to navigate:

## Start Here
- [Overview](overview.md)
- [Architecture](architecture.md)

## Guides
- [Dependencies](dependencies.md)
- [Data Flow](data-flow.md)

## Modules
- [Module A](modules/module-a.md)
- [Module B](modules/module-b.md)

## Glossary
- [Glossary](glossary.md)
```

## Update rules

- Keep links relative to `deepwiki/`.
- Avoid deleting user-added sections; append with "Update" subsections if unsure.
- Prefer stable filenames; only add new module pages when a new module is discovered.
