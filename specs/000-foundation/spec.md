# Feature Specification: M0 — Repository foundation

**Feature Branch**: No branch created; existing branch `main` retained.

**Created**: 2026-10-27

**Status**: Draft; human review required before implementation. First milestone.

**Input**: Specify the existing student-planner repository's local-first PWA foundation using React, TypeScript, Vite, Dexie.js and a minimal Python 3.11+ FastAPI backend with uv, pytest and ruff. Include frontend testing, linting and type checking; preserve the repository and documentation. Specification only; no application implementation.

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Start the local frontend (Priority: P1)

As a contributor, I can start a minimal planner shell locally so later approved planner work has a stable starting point.

**Why this priority**: The frontend must run independently of accounts, cloud services and the backend.

**Independent Test**: Follow frontend setup on a clean checkout with documented prerequisites installed, keeping the backend stopped.

**Acceptance Scenarios**:

1. **Given** a clean checkout and documented prerequisites, **When** dependencies are installed and the frontend is started, **Then** the page displays the planner identity and a main content landmark without task controls or uncaught application errors.
2. **Given** no running backend or cloud credentials, **When** the locally served shell is opened and reloaded, **Then** it renders without authentication prompts or backend/cloud requests.
3. **Given** the frontend scaffold, **When** a production build is generated and previewed locally, **Then** the same minimal shell renders successfully.

---

### User Story 2 - Verify browser-local storage (Priority: P1)

As a contributor, I can verify local storage initialization so later milestones can add persistence without choosing a cloud provider.

**Why this priority**: Local storage is foundational; task behavior belongs to M1.

**Independent Test**: Run isolated initialization tests and open the shell in a fresh browser profile with database access available.

**Acceptance Scenarios**:

1. **Given** a fresh profile with browser database support, **When** storage initializes, **Then** it succeeds without external services, seeded planner records or task operations.
2. **Given** initialized storage, **When** initialization repeats, **Then** it succeeds without creating additional database instances or fixture records.
3. **Given** database access is denied or unavailable, **When** initialization is attempted, **Then** the shell remains visible with an accessible storage-unavailable message and no remote fallback is attempted.

---

### User Story 3 - Check the independent backend (Priority: P2)

As a contributor, I can run a minimal local backend and check its health without configuring a database or planner services.

**Why this priority**: This prepares the agreed server boundary without making the frontend depend on it.

**Independent Test**: Start the backend without the frontend or credentials and run its health test.

**Acceptance Scenarios**:

1. **Given** installed backend prerequisites and dependencies, **When** the backend starts locally and receives `GET /health`, **Then** it returns HTTP 200 and JSON `{"status":"ok"}` without external service access.
2. **Given** the backend route inventory, **When** it is reviewed, **Then** `/health` is the only application-defined endpoint; framework-generated documentation routes are permitted, and task/account routes are absent.

---

### User Story 4 - Reproduce checks and review the handoff (Priority: P2)

As a maintainer, I can reproduce the foundation checks and review evidence so M0 completion rests on verified results.

**Why this priority**: Later work needs repeatable checks and accurate setup instructions.

**Independent Test**: Follow README commands from a clean checkout and compare outcomes with the progress record and repository inventory.

**Acceptance Scenarios**:

1. **Given** installed dependencies, **When** frontend tests, linting, formatting verification, type checking and production build run, **Then** every check exits successfully; tests cover shell rendering and all three storage scenarios.
2. **Given** the backend scaffold, **When** backend tests and lint/format checks run, **Then** every check exits successfully and a test asserts the health response status and body.
3. **Given** completed implementation checks, **When** the README and progress log are reviewed, **Then** prerequisites, exact executed commands, outcomes and limitations are recorded without claiming offline installation, deployment or synchronization.
4. **Given** a proposed scaffold, **When** human validation occurs, **Then** obsolete artifacts are identified for approval before removal; after approved cleanup, imports and the directory tree are inspected and removed items or “none” are recorded.

### Edge Cases

- Existing files or uncommitted work: inspect before scaffolding; reuse compatible configuration and preserve unrelated content without wholesale generator replacement.
- Storage unavailable or denied: show the failure described in Story 2; never silently claim persistence or use cloud fallback.
- Backend stopped: frontend startup and local storage remain independent, as in Story 1.
- Missing prerequisites or occupied ports: setup instructions identify required runtimes and explain how to resolve a local port conflict; record success only after actual execution.
- Initial dependency installation may require the network. Offline shell loading without a local asset server and browser-data eviction recovery are outside M0 acceptance.

## Requirements *(mandatory)*

### Functional Requirements

- **FR-001**: M0 MUST preserve the existing layout, root instructions, documentation and unrelated milestone drafts. This file MUST remain the sole canonical M0 specification, with `.specify/feature.json` pointing to `specs/000-foundation`. Acceptance: repository inventory, pointer and documentation-link inspection.
- **FR-002**: Contributors MUST be able to install, start, build and preview a minimal frontend independently of the backend and account/cloud services. Acceptance: Story 1.
- **FR-003**: Local storage MUST support initialization, repeat initialization and visible failure without planner records or task CRUD. Acceptance: Story 2.
- **FR-004**: Contributors MUST be able to start a backend whose only application-defined endpoint is the health check, without credentials or external services. Acceptance: Story 3.
- **FR-005**: The scaffold MUST provide frontend tests, linting, formatting verification, type checking and production build, plus backend tests and lint/format checks. Checks MUST exit nonzero on detected errors. Acceptance: Story 4 scenarios 1–2 and command configuration review.
- **FR-006**: After implementation, documentation MUST record prerequisites and exact verified commands/results, retain the canonical M0 link, and distinguish implemented from planned behavior. Acceptance: Story 4 scenario 3 and documentation review.
- **FR-007**: Implementation MUST follow propose → human validation → approved cleanup, inspect remaining imports and directories, and report redundant artifacts removed or none found. Acceptance: Story 4 scenario 4.

### Required Technology and Repository Constraints

These explicit user/project constraints intentionally override the generic specification preference to omit technology names. Internal design belongs in the plan.

- Frontend: React, strict TypeScript and Vite under `frontend/src/`; IndexedDB via Dexie.js for initialization and a minimal typed storage boundary only. No speculative task interfaces, CRUD, migration framework or sync adapter.
- Preserve existing M0 styling scope: Tailwind CSS with semantic surface, text, border, accent and status tokens. No theme selector, catalog, downloaded font collection or customization editor.
- Vitest and React Testing Library are existing proposed test defaults; ESLint and TypeScript checks follow the README direction. Planning must select a formatting tool and test placement under `frontend/src/` or `frontend/tests/`.
- Backend: Python 3.11+, FastAPI and uv under `backend/src/<package>/`, pytest tests under `backend/tests/`, and ruff lint/format checks. The health contract is defined in Story 3.
- Keep dependency declarations and repeatable installation metadata in the respective subtrees. Follow AGENTS.md typing, documentation and function/file size rules; avoid loose root scripts, duplicate implementations and unused generated demo assets.

### Scope Boundaries

- This workflow updates the specification and feature selection metadata only; it does not authorize or perform application implementation.
- Future approved M0 implementation delivers only the shell, storage initialization, health check and development tooling described here.
- Task capture, CRUD, scheduling, rollover, recurrence, drag-and-drop, projects, tags, search and recovery remain later milestones.
- Authentication, Supabase, Dexie Cloud, cloud synchronization, remote database configuration, deployment and hosting provisioning are excluded.
- PWA manifest/installability acceptance, service-worker caching, offline shell loading and export remain M5 work. M0 is the development foundation for that PWA.
- CI, branch automation, Pomodoro, calendars, rewards and speculative endpoints are excluded from this slice.

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: A reviewer completes documented frontend setup, local launch and production preview from a clean checkout with zero undocumented setup steps; both shells render with zero uncaught application errors and no running backend or cloud credentials.
- **SC-002**: All three local storage acceptance scenarios pass, with zero seeded planner records and zero remote fallback requests.
- **SC-003**: The independent backend health check passes with exactly one application-defined endpoint and zero required external services.
- **SC-004**: Every required automated check exits successfully; the handoff records the exact command and actual outcome for each, with no failed or unexecuted check reported as passing.
- **SC-005**: Review finds exactly one M0 specification, zero changes to unrelated milestone content and zero unapproved removals. A human reviewer reproduces the setup and accepts the scope before M0 is marked complete.

## Assumptions

- M0 users are contributors and maintainers; student-facing planner flows begin later.
- AGENTS.md, docs/ARCHITECTURE.md, docs/ROADMAP.md and the existing M0 draft provide the governing context. Other milestone drafts do not authorize implementation.
- `.specify/memory/constitution.md` contains template placeholders and is not a ratified constitution; it adds no adopted principles.
- Existing frontend/backend directories are empty at specification time. Implementation must inspect them again and reuse any intervening work.
- Dependency installation may require network access. Local execution needs installed dependencies, documented supported runtimes and a browser with IndexedDB. Exact runtime versions and remaining tooling choices belong in planning.
- Durable task persistence, migration policy, export and eviction recovery require their later approved scopes.
- This draft approves no new architecture decision. Update decision documentation for subsequently approved changes and progress documentation with actual verified outcomes.
