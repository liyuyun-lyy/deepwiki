# Overview

## Purpose
- Generate and update deepwiki docs for a repository.
- Provide a predictable `/deepwiki` CLI workflow.

## Repo Layout
- `src/cli/` handles command parsing and execution.
- `src/generator/` builds markdown pages.

## Entry Points
- `src/cli/main.ts` wires `/deepwiki` commands.

## Where to Start
- Read `README.md` for install and usage.
- Run `/deepwiki:index` to build the initial index.

## How to Navigate
- Start with `deepwiki/INDEX.md`, then follow module links grouped by theme.

## Index Structure
- Build & Development
  - Package Structure and Dependencies
  - Build Tasks and Scripts
  - Native Modules and Cross-Platform Builds
  - Release and Packaging Pipeline
- Application Lifecycle
  - Entry Points and Execution Modes
  - Startup and Bootstrap Sequence
  - Shutdown and Cleanup
- Architecture
  - Multi-Process Architecture
  - Service Initialization and Dependency Injection
  - Workbench Architecture
  - Extension Host and Contribution System
- UI System
  - Layout System and Parts
  - Editor Service and Groups
  - Editor Input and Pane System
  - Action and Menu System
  - Context Keys and State Management
  - View System and Contributions
- Platform & Runtime
  - Configuration and Settings
  - Telemetry and Diagnostics
  - Security and Trust Model
- Modules
  - Monaco Editor Core
  - Text Model and View Model
  - Search and Indexing
  - File System Providers
  - Language Services
  - Debug Adapter Protocol

## Diagrams
```mermaid
flowchart LR
  Repo[Repository] --> Index[Dynamic INDEX]
  Index --> Pages[Deepwiki Pages]
```

## Missing Image Reporting
- Missing image: `docs/architecture.md` → `assets/mermaid3.jpg` (blocked: path escapes repo root)

## Source References
- README.md
- src/cli/main.ts
