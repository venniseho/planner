# Roadmap

**Planning is not implementation.** Check milestones only after tests and human validation. Keep work in small Spec Kit features; do not ask Codex to build Phase 1 in one pass.

| Phase | Milestones | Exit criteria |
|---|---|---|
| 0 — Foundation | **M0** Confirm docs/standards; scaffold frontend + local-only minimal backend and tooling | Runs locally; lint/test commands pass; no speculative endpoints |
| 1 — Local planner | **M1** Task quick-add → local persistence → planned-date board; **M2** editing, rollover, Upcoming, sidebar and ordering; **M3** projects/groups, subtasks and tags; **M4** recurrence, priority, deletion/recovery, search/filter and theme/font preferences and basic UI settings; **M5** appearance foundation and selectable starter palettes/fonts, offline app shell/export and Cloudflare deployment | Phase 1 acceptance tests, browser reload/offline checks, user review; no sync claims |
| 2 — Cross-device | Select cloud/sync/auth, build account migration and privacy; concurrency, conflict, tombstones, backups | Verified same records on two devices and offline reconciliation |
| 3 — Focus/metrics | Pomodoro with task lists, focus tracking, project charts | Tested session/task accounting |
| 4 — Integrations/rewards | Google Calendar aggregation/free-busy sharing, self-set rewards, gamification | Permission/privacy review, tested integrations |

## M0: first setup milestone

- Reuse existing repo if present; review folders before scaffolding.
- Setup React + TypeScript + Vite, styling tokens, test and lint tools.
- Setup Dexie local data adapter but no sync adapter implementation.
- Minimal FastAPI scaffold only (`/health`), uv + pytest + ruff; don't deploy Python.
- Preserve root `AGENTS.md` standards; verify commands and document them in README only after running.
- Configure branch/commit conventions and CI as a separate focused change if needed.

## M1: first product milestone

1. Create a title-only task from inbox; Enter and Save work.
2. Persist locally; reload keeps task.
3. Schedule task via date picker into today…today+6 and show it in correct Kanban column.
4. Edit planned date; verify it moves without cloning.
5. Date handling, required-title validation, keyboard focus, and basic accessibility tested.
6. Validate with user, immediately prune unused code, update PROGRESS and documented commands.

Reference: [M1 specification](../specs/001-local-task-slice/spec.md).

## Deferred phase gates

- Phase 2 starts only after a documented free-tier/cloud-sync evaluation and a tested migration/backup strategy.
- New features from [IDEAS](IDEAS.md) do not become milestones without an explicit scope decision.

See [customization vision](CUSTOMIZATION.md) for the complete theme/font goal and what remains deferred.

## Milestone specification index

| Milestone | Specification |
|---|---|
| M0 | [Foundation](../specs/000-foundation/spec.md) |
| M1 | [Local task slice](../specs/001-local-task-slice/spec.md) |
| M2 | [Board and task discovery](../specs/002-planner-board/spec.md) |
| M3 | [Projects, groups, tags and subtasks](../specs/003-organization/spec.md) |
| M4 | [Task lifecycle, recurrence and search](../specs/004-task-lifecycle/spec.md) |
| M5 | [Appearance, offline and deployment](../specs/005-appearance-offline-deploy/spec.md) |

**Customization staging:** Desired catalog includes light/dark, pastel and red–purple colors, aesthetic presets and custom theme editors. M5 implements design tokens and an approved, limited starter selector; extensive curated catalog and editors require their own later specs. Do not claim the full catalog ships in Phase 1.
