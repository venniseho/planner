# M2 — Rolling board, Upcoming and task drawer

**Status:** Draft; human review required before implementation. **Sequence:** after earlier milestone validation.

## Goal

Make tasks easy to plan without time blocking.

## In scope

- Show seven date-only Kanban columns for today through today+6; allow pointer drag/drop to a day and within-day reorder, with a click/date-picker alternative.
- Unfinished ordinary tasks from earlier planned dates render in Today without rewriting stored `planned_date`; deliberate move does update it.
- Upcoming: unscheduled incomplete tasks due within seven days plus overdue unscheduled tasks as actionable cards; scheduled due-soon tasks as compact list.
- Sidebar: show five relevant unscheduled tasks with View all; Later lists planned dates past the seven-day window, ordered by date.
- Manual saved order is default; due-date/project sort is optional and must not overwrite saved manual order.
- Display small gray due-date text; only badges/flags change color for due today, overdue or completed; task cards retain theme.

## Acceptance criteria

1. Rollover across day boundary moves display but not persisted date; editing changes persisted date.
2. Drag to day and click schedule yield identical record without duplication; order survives refresh.
3. Upcoming displays scheduled and unscheduled records in their proper formats and no duplicate entities.
4. No-date tasks remain accessible in Unscheduled; Later is driven by planned date, not due date.
5. Tests cover date windows/timezone transitions, overdue status and accessibility of schedule alternative.

## Not in scope

- Cloud authentication/sync, custom remote APIs, Pomodoro, gamification and calendar integration unless separately specified.
- Unrequested helpers, parallel implementations, or speculative migration layers.

## Engineering / handoff

Implement as a small Spec Kit/Codex slice, not the whole milestone at once. Respect root `AGENTS.md`, existing files, typed functions, tests and human validation. After verification update `docs/PROGRESS.md`, relevant decision docs, and README; remove obsolete code only after approval.
