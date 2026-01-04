---

description: "Task list for Local Image Support"
---

# Tasks: Local Image Support

**Input**: Design documents from `/specs/001-image-support/`
**Prerequisites**: plan.md (required), spec.md (required), research.md, data-model.md, contracts/, quickstart.md

**Tests**: Not requested in the feature specification.

**Organization**: Tasks are grouped by user story to enable independent implementation and testing of each story.

## Format: `[ID] [P?] [Story] Description`

- **[P]**: Can run in parallel (different files, no dependencies)
- **[Story]**: Which user story this task belongs to (e.g., US1, US2, US3)
- Include exact file paths in descriptions

## Path Conventions

- Skill and template work lives under `skills/deepwiki/`
- Spec updates remain under `specs/001-image-support/`

## Phase 1: Setup (Shared Infrastructure)

**Purpose**: Align skill scope and documentation expectations

- [ ] T001 Confirm skill is the primary delivery mechanism and update scope in `specs/001-image-support/plan.md`
- [ ] T002 [P] Add mermaid-in-Markdown requirements to `specs/001-image-support/spec.md`
- [ ] T003 [P] Update research decisions in `specs/001-image-support/research.md`

---

## Phase 2: Foundational (Blocking Prerequisites)

**Purpose**: Define baseline behavior in the skill contract

**⚠️ CRITICAL**: No user story work can begin until this phase is complete

- [ ] T004 Update image handling rules in `skills/deepwiki/SKILL.md`
- [ ] T005 Define mermaid block handling in `skills/deepwiki/SKILL.md`

**Checkpoint**: Foundation ready - user story implementation can now begin in parallel

---

## Phase 3: User Story 1 - View Local Images in Docs (Priority: P1) 🎯 MVP

**Goal**: Render local images inline in generated documentation pages.

**Independent Test**: Use a source page that references `mermaid1.jpg` and confirm the generated deepwiki page embeds the local image.

### Implementation for User Story 1

- [ ] T006 [US1] Add local image guidance to templates in `skills/deepwiki/templates/architecture.md`
- [ ] T007 [US1] Add local image guidance to templates in `skills/deepwiki/templates/data-flow.md`
- [ ] T008 [US1] Add example local image usage in `skills/deepwiki/examples/architecture-example.md`
- [ ] T009 [US1] Add example local image usage in `skills/deepwiki/examples/data-flow-example.md`

**Checkpoint**: User Story 1 should be fully functional and testable independently

---

## Phase 4: User Story 2 - Preserve Image Context (Priority: P2)

**Goal**: Preserve alt text or captions for local images.

**Independent Test**: Use an example with alt text and confirm it appears in the generated example output.

### Implementation for User Story 2

- [ ] T010 [US2] Document alt text expectations in `skills/deepwiki/SKILL.md`
- [ ] T011 [US2] Add alt text usage example in `skills/deepwiki/examples/architecture-example.md`

**Checkpoint**: User Stories 1 AND 2 should both work independently

---

## Phase 5: User Story 3 - Handle Missing Images Gracefully (Priority: P3)

**Goal**: Require actionable reporting for missing or blocked images.

**Independent Test**: Document a missing-image case in the skill guidance and ensure the example shows the expected reporting format.

### Implementation for User Story 3

- [ ] T012 [US3] Add missing-image reporting guidance in `skills/deepwiki/SKILL.md`
- [ ] T013 [US3] Add missing-image reporting example in `skills/deepwiki/examples/overview-example.md`

**Checkpoint**: All user stories should now be independently functional

---

## Phase 6: Polish & Cross-Cutting Concerns

**Purpose**: Consistency across templates, quickstart, and parity

- [ ] T014 [P] Add mermaid block examples to `skills/deepwiki/examples/module-example.md`
- [ ] T015 [P] Update quickstart validation notes in `specs/001-image-support/quickstart.md`
- [ ] T016 [P] Add parity checklist note in `specs/001-image-support/spec.md`

---

## Dependencies & Execution Order

### Phase Dependencies

- **Setup (Phase 1)**: No dependencies - can start immediately
- **Foundational (Phase 2)**: Depends on Setup completion - BLOCKS all user stories
- **User Stories (Phase 3+)**: All depend on Foundational phase completion
- **Polish (Final Phase)**: Depends on all desired user stories being complete

### User Story Dependencies

- **User Story 1 (P1)**: Can start after Foundational (Phase 2) - No dependencies on other stories
- **User Story 2 (P2)**: Can start after Foundational (Phase 2) - Builds on US1 examples
- **User Story 3 (P3)**: Can start after Foundational (Phase 2) - Shares reporting guidance from core

### Within Each User Story

- Update templates before examples
- Example output should align with skill rules

### Parallel Opportunities

- T002 and T003 can run in parallel
- T006 and T007 can run in parallel
- T008 and T009 can run in parallel
- T014, T015, T016 can run in parallel

---

## Parallel Example: User Story 1

```bash
Task: "Add local image guidance to templates in skills/deepwiki/templates/architecture.md"
Task: "Add local image guidance to templates in skills/deepwiki/templates/data-flow.md"
```

---

## Implementation Strategy

### MVP First (User Story 1 Only)

1. Complete Phase 1: Setup
2. Complete Phase 2: Foundational
3. Complete Phase 3: User Story 1
4. **STOP and VALIDATE**: Confirm examples reference local images

### Incremental Delivery

1. Complete Setup + Foundational → Foundation ready
2. Add User Story 1 → Validate examples → Demo
3. Add User Story 2 → Validate alt text usage
4. Add User Story 3 → Validate missing-image reporting guidance
5. Final polish for templates and parity
