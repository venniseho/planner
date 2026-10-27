# M3 — Projects, groups, subtasks and global tags

**Status:** Draft; human review required before implementation. **Sequence:** after earlier milestone validation.

## Goal

Organize syllabus-style work while preserving quick entry and project progress.

## In scope

- Add optional project groups containing projects, with projects optionally ungrouped.
- Tasks may belong to one optional project and have one optional parent; limit to one subtask level, inheriting project affiliation.
- Subtasks and top-level tasks can each have planned/due dates; only top-level tasks count for project completion percent.
- Parent task completion is always manual, even if all children are complete; child counts may be shown separately.
- Global tags are reusable across groups/projects, have optional colors, and form many-to-many task associations; removing a tag does not delete its tasks.
- Task creation from a project preselects that project; quick-add remains title-only with optional More options.

## Acceptance criteria

1. Projects/groups may be created, renamed and used without mandatory parent groups.
2. Parent with three complete subtasks remains incomplete until manually checked; progress counts top-level tasks once.
3. Cross-project global tag works and deletion of association leaves tasks intact.
4. Subtask depth limit, inheritance and record reload verified with tests.

## Not in scope

- Cloud authentication/sync, custom remote APIs, Pomodoro, gamification and calendar integration unless separately specified.
- Unrequested helpers, parallel implementations, or speculative migration layers.

## Engineering / handoff

Implement as a small Spec Kit/Codex slice, not the whole milestone at once. Respect root `AGENTS.md`, existing files, typed functions, tests and human validation. After verification update `docs/PROGRESS.md`, relevant decision docs, and README; remove obsolete code only after approval.
