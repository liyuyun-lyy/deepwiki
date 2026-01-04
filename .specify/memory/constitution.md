<!--
Sync Impact Report
- Version change: template -> 0.1.0
- Modified principles: [PRINCIPLE_1_NAME] -> I. Progressive, Document-Driven Pipeline; [PRINCIPLE_2_NAME] -> II. Repository-Local Parsing; [PRINCIPLE_3_NAME] -> III. Deterministic and Traceable Outputs; [PRINCIPLE_4_NAME] -> IV. Minimal Steps, CLI-First; [PRINCIPLE_5_NAME] -> V. Modular Stages with Clear Contracts
- Added sections: Deepwiki Generation Stages; Workflow and Quality Gates
- Removed sections: None
- Templates requiring updates: ✅ updated .specify/templates/plan-template.md; ✅ updated .specify/templates/spec-template.md; ✅ updated .specify/templates/tasks-template.md
- Follow-up TODOs: TODO(RATIFICATION_DATE): initial adoption date unknown
-->
# Deepwiki Kit Constitution

## Core Principles

### I. Progressive, Document-Driven Pipeline
Deepwiki generation MUST be a staged pipeline where each step reads the prior
step's artifacts and writes new artifacts. No step may silently skip required
inputs; missing or stale inputs MUST fail fast with actionable errors.
Rationale: Progressive execution keeps the process explainable and debuggable.

### II. Repository-Local Parsing
All analysis MUST come from the local repository: directory structure, source
code, configuration, and docs. Network access is forbidden by default and only
allowed when explicitly configured and documented in outputs.
Rationale: Local-only parsing preserves reproducibility and privacy.

### III. Deterministic and Traceable Outputs
Given the same repository state and configuration, outputs MUST be deterministic.
Every run MUST emit a manifest with repository identifier (commit hash or ref),
tool version, and stage timestamps.
Rationale: Determinism enables verification, caching, and safe regeneration.

### IV. Minimal Steps, CLI-First
Deepwiki generation MUST be achievable in a small number of CLI steps. Each step
MUST be idempotent and provide human-readable output plus optional JSON.
Rationale: Few steps reduces operator friction and supports automation.

### V. Modular Stages with Clear Contracts
Each stage MUST declare its inputs, outputs, and side effects, and MUST be
replaceable without rewriting other stages.
Rationale: Modular contracts keep the pipeline extensible and maintainable.

## Deepwiki Generation Stages

1. **Repository Intake**: Generate a directory tree and inventory files,
   respecting ignore rules.
2. **Parsing and Indexing**: Extract language stats, symbols, dependencies,
   and documentation anchors.
3. **Summarization and Linking**: Produce module summaries and cross-linking
   data between components.
4. **Rendering**: Emit markdown pages and navigation scaffolding in `deepwiki/`.
5. **Validation**: Check for missing pages, broken links, and manifest integrity.

## Workflow and Quality Gates

- Each stage writes its artifacts under `deepwiki/` with a manifest entry.
- Stages MUST be independently runnable for troubleshooting.
- A release is valid only if Repository Intake, Parsing and Indexing, Rendering,
  and Validation stages succeed.
- A sample "golden repo" test suite MUST cover at least one full pipeline run.

## Governance
This constitution is the source of truth for deepwiki-kit behavior. Amendments
require a documented proposal, rationale, and migration impact. Versioning uses
Semantic Versioning: MAJOR for breaking principle changes, MINOR for new
principles or sections, PATCH for clarifications. All specs, plans, and tasks
MUST include a constitution check before execution. Runtime usage guidance lives
in `README.md`.

**Version**: 0.1.0 | **Ratified**: TODO(RATIFICATION_DATE): initial adoption date unknown | **Last Amended**: 2026-01-04
