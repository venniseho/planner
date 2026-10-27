# M1 Feature specification: local task creation and scheduling

**Status:** Draft for Spec Kit review. **Depends on M0 scaffold.** No backend or cloud service required.

## User story

As a student, I want to add a task with just a title, optionally assign a day, see it in my seven-day board, and have it still exist after refreshing, so planning does not require time blocking.

## Scope

- Quick add in Unscheduled: required nonblank title; save via Enter or Save; optional More options opens a detail editor (initial scope: planned date only, other fields follow in later slices).
- Newly created task has client-generated stable ID, `is_completed=false`, `planned_date=null`, timestamps (implementation-level metadata).
- Save title-only task to Dexie/IndexedDB; list under Unscheduled; focus remains in add input for rapid entry.
- Assign or edit `planned_date` via accessible date picker; show on today…today+6 board. Task persists after reload. Kanban creation context may prefill the day and close editor on save.
- Seven date columns are rolling local calendar dates. No need for timed appointments or cloud accounts.

## Out of scope

Projects/groups/tags, recurrence, drag reorder, overdue badges, all-device sync, authentication, service worker, backend task CRUD, project progress, calendar integrations, gamification. They have separate milestones.

## Acceptance scenarios

1. Enter title "Finish outline" and press Enter → exactly one saved task, visible in Unscheduled, title input ready for another entry.
2. Empty/whitespace title → no created task; accessible validation feedback.
3. Reload application → saved task survives and keeps its ID.
4. Set planned date to tomorrow via date picker → task appears in tomorrow column and leaves Unscheduled; no duplicate record.
5. Edit same planned date to today → same ID appears today, remains after reload.
6. Clear planned date → task returns to Unscheduled without deletion.
7. On narrow viewport, board remains navigable and task input/labels usable with keyboard and pointer.
8. `Enter` in title saves; `Esc` can dismiss a modal/details context; keyboard shortcuts do not hijack normal text editing.
9. Automated tests cover persistence adapter, required title, date-only mapping and view selection; run actual lint/type-check/test commands and log results.

## Engineering constraints

- Keep presentation independent of Dexie implementation via a small typed task-access boundary; no speculative abstraction stack.
- No schema assumptions that require a cloud provider. Make date-only values unambiguous.
- Surgical edits only; user validation before removing obsolete code; record implementation in `docs/PROGRESS.md` after verification.

## Handoff to Spec Kit

Use the repo's actual slash-command syntax once Spec Kit is initialized. Suggested focused requirement string:

> `/specify Implement M1 from specs/001-local-task-slice/spec.md only: title-only quick-add, IndexedDB persistence through Dexie, Unscheduled list, editable planned date, and 7-day rolling board. Use typed domain boundary, no backend or sync, preserve keyboard interactions, validate acceptance cases and avoid speculative files.`
