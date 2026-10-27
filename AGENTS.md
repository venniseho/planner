# Agent Instructions

## 1. Working Mode

- Work from one approved `specs/` milestone and its linked documentation at a time. Never implement future phases speculatively.
- Follow: **Propose → Human review/validation → Prune obsolete code.**
- Make surgical changes. Prefer modifying existing files and functions over creating new ones.
- Do not introduce duplicate implementations, speculative helpers, or unnecessary modules.
- Phase 1 is **local-first**. Do not implement authentication, Supabase, Dexie Cloud, cloud synchronization, or deploy FastAPI without a separately approved specification.

## 2. Code Architecture & Hygiene

- Keep functions under 30 lines, with one responsibility per function.
- Maintain one primary logical concept per file. Refactor files exceeding 200 lines into focused modules.
- Use clear, descriptive identifiers. Standard conventions such as `df`, `t`, and `x` are acceptable.
- Require strict argument and return types.
- Use concise Google-style docstrings for Python functions, classes, and public modules. Use TSDoc/JSDoc equivalents for TypeScript.
- Never leave dead code, unused imports, orphaned files, or backups (`.old`, `.bak`, `_v2`).
- After human validation, immediately remove superseded implementations.
- Before completing any task, inspect imports and the directory tree. Report redundant code/files removed, or explicitly state that none were found.

## 3. Project Structure & Tooling

- **Frontend:** React + TypeScript under `frontend/src/`; tests colocated or under `frontend/tests/` according to the validated setup.
- **Backend:** Python 3.11+ under `backend/src/<package>/`; tests under `backend/tests/`.
- **Python tooling:** `uv`, `pytest`, `ruff`.
- **Frontend tooling:** Use the configured TypeScript testing, linting, and formatting tools.
- **Local persistence:** IndexedDB via Dexie.js.
- **Hosting:** Cloudflare, when deployment is approved.
- Do not scatter loose scripts or modules in the repository root.

## 4. Testing & Validation

- Test behavior and relevant edge cases, especially CRUD, date rollover, recurrence, drag-and-drop, and keyboard interactions.
- Run applicable tests, linting, and type checks before requesting acceptance.
- Never claim tests pass unless they were executed successfully.
- Report validation results and remaining limitations.
- Do not remove superseded code before human approval, unless the approved specification explicitly includes that removal.

## 5. Git Conventions

- Branch names must be lowercase, short, and no more than three words, using formats such as `feature/task-add` or `fix/date-rollover`.
- Commit messages must be single-line Conventional Commits.
- Allowed commit types: `feat`, `fix`, `docs`, `refactor`, `test`.
- Example: `feat: add local task persistence`.

## 6. Documentation & Progress Tracking

- `README.md`: Comprehensive project overview and entry point.
- `docs/ARCHITECTURE.md`: System design, technical boundaries, and diagrams.
- `docs/DATA_MODEL.md`: Entities, relationships, and persistence rules.
- `docs/DECISIONS.md`: Approved architecture and design decisions.
- `docs/ROADMAP.md`: Milestones, priorities, and planned scope.
- `docs/PROGRESS.md`: Verified implementation progress, tests, and blockers.
- `docs/CUSTOMIZATION.md`: Themes, typography, and appearance architecture.
- `docs/IDEAS.md`: Deferred features and nice-to-haves.
- `specs/`: Feature-specific requirements and acceptance criteria.

Use M0–M5 specifications as sequential planning drafts, not blanket authorization for implementation.

Update documentation only when relevant:
- Record changed design decisions in `DECISIONS.md`.
- Record verified implementation results in `PROGRESS.md`.
- Update affected feature specifications when behavior changes.
- Keep the README synchronized at a summary level without duplicating entire specifications.

## 7. Completion Requirements

Before declaring an implementation task complete:

1. Verify the implementation against its approved specification.
2. Run relevant automated checks and report actual results.
3. Request human validation when required.
4. After approval, prune obsolete code and verify the remaining imports and structure.
5. Update the appropriate progress and decision documentation.
6. Summarize the changes, validation results, and any remaining issues.