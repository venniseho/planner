# M4 — Recurrence, priority, deletion, search and filters

**Status:** Draft; human review required before implementation. **Sequence:** after earlier milestone validation.

## Goal

Add routine task behaviors without turning the planner into a heavyweight scheduler.

## In scope

- Basic recurring rules: daily, chosen weekdays, weekly, monthly. Materialize independent occurrences with stable deduplication keys; no duplicated new occurrences after reopening.
- Recurring rollover toggle defaults OFF; missed occurrences remain incomplete in history but do not pile into Today; when ON ordinary rollover applies to unfinished occurrences.
- Keep `is_completed` as stored boolean; derive due-today/overdue and completed badges; expose simple important flag while reserving priority data for future levels.
- Soft-delete with `deleted_at`, show 10-second Undo via notification and Ctrl/Cmd+Z outside text editing, offer small Settings restore access for 14 days, then eligible cleanup.
- Search title/description and filter by project, group, tag, completion and importance; defaults are proposed, adjust on validation.
- Completed tasks remain accessible using filters but out of active default views (proposed).

## Acceptance criteria

1. Reopening on same day does not generate duplicate recurring occurrences.
2. Monday recurring task missed with rollover OFF does not create a second Monday card on Tuesday; Tuesday occurrence still appears.
3. Undo restores same record and associations; 14-day retention/eligibility behavior tests use controllable clock.
4. Ctrl/Cmd+Z inside text fields retains native editor Undo.
5. No deletion resurrection during local reload; remote sync tombstones remain a Phase 2 decision.

## Not in scope

- Cloud authentication/sync, custom remote APIs, Pomodoro, gamification and calendar integration unless separately specified.
- Unrequested helpers, parallel implementations, or speculative migration layers.

## Engineering / handoff

Implement as a small Spec Kit/Codex slice, not the whole milestone at once. Respect root `AGENTS.md`, existing files, typed functions, tests and human validation. After verification update `docs/PROGRESS.md`, relevant decision docs, and README; remove obsolete code only after approval.
