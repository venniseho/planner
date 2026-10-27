# Decision log

**Legend:** `Agreed` = explicitly selected during planning; `Proposed` = starting default awaiting UI/testing validation; `Deferred` = must be decided before relevant implementation. Detailed behavior belongs in specs, not this log.

| ID | State | Decision / rationale |
|---|---|---|
| D01 | Agreed | Personal-first, product-ready architecture; cost-conscious and adaptable to multiple users. |
| D02 | Agreed | Seven rolling day columns (today … today+6), not rigid time blocking. Calendar is the future time-blocking area. |
| D03 | Agreed | `planned_date` and optional `due_date` are independent; both directly editable. |
| D04 | Agreed | Incomplete ordinary tasks roll into today's **display**, not a midnight rewrite of `planned_date`; explicit edits change date. |
| D05 | Agreed | Upcoming above board: unscheduled deadline tasks as actionable cards, already scheduled deadlines as compact list; due within seven days, and overdue unscheduled stay visible. |
| D06 | Agreed | Sidebar/drawer: compact Unscheduled (top tasks with View all) and Later (planned outside board). Later is not a due-date bucket. |
| D07 | Agreed | Manual task ordering, with optional due-date/project sort; drag/drop and click-to-schedule. |
| D08 | Agreed | One optional project per task; optional project groups; zero-or-more global, reusable, recolorable tags. |
| D09 | Agreed | Tasks can be standalone or have one level of subtasks; parent completion is manual; project progress counts completed **top-level** tasks only. |
| D10 | Agreed | Completion stored simply; deadline labels computed. Incomplete normal tasks show no badge; Due today amber, Overdue red, Completed green; recolor badge/flag only, never theme-styled card. |
| D11 | Agreed | Quick-add title then Save or More options; Enter saves; creation context supplies project/day; post-save behavior depends on UI context. |
| D12 | Agreed | 10-second deletion Undo and Ctrl/Cmd+Z when not editing text. Soft delete, minimal Settings recovery, 14-day recovery window then eligible for cleanup. No move/reschedule Undo. |
| D13 | Agreed | Basic recurring occurrences (daily, selected weekday(s), weekly, monthly), independently completed; recurrence rollover toggle OFF by default, missed nonrolled instances retained. |
| D14 | Agreed | Phase 1 exposes important/unflagged; priority data model allows future levels. Future mode switches should avoid data loss and warn before destructive conversion. |
| D15 | Agreed | React/TypeScript primary UI; minimal Python/FastAPI scaffold; Cloudflare preferred host; synced multi-device access required in Phase 2. |
| D16 | Agreed | Strong README with project motivation, architecture, linked detailed docs, tradeoffs, development process, and verified progress. |
| D17 | Proposed | Search title/description, case-insensitive; filters for project/group/tag/completion/important; clear-all; avoid speculative query UI. |
| D18 | Proposed | Subtasks expand inline; edit details in a focused panel; completed tasks hidden from active default views but available via filters/project lists. |
| D19 | Agreed direction / staged scope | Light/dark plus pastel and rainbow color themes; curated aesthetic presets (Green Botanist, Light/Dark Academia, Starry Night); editable color themes and custom presets; selectable contrasting font styles. Implement gradually with token architecture; exact Phase 1 catalog remains proposed. |
| D20 | Proposed | Show five unscheduled tasks prioritizing overdue/near due; optional sorting should not destroy saved manual order. |
| D21 | Deferred | Supabase/PostgreSQL vs Dexie Cloud vs alternatives; free-tier sustainability, syncing, conflict semantics, exports/backups, inactivity, user limits. **Gate before Phase 2.** |
| D22 | Deferred | Auth provider, cloud ownership authorization, multi-device deletion propagation and tombstone retention, initial local-data migration to account. |
| D23 | Deferred | Exact Cloudflare deployment target (Pages vs Workers), PWA offline-asset caching, production monitoring; validate when implementing deployment. |

| D24 | Proposed | Typography starter set: DM Sans (sans), Space Grotesk (contrasting sans), Cormorant Garamond (elegant serif), Courier Prime (typewriter serif), JetBrains Mono (code-style). Verify licensing, legibility and offline assets before bundling. |
| D25 | Proposed | Separate palette, font, and composite preset preferences; custom theme editors and the full aesthetic preset library are staged beyond the first functional theme selector. |

**Rule:** proposed UX defaults can change after user validation; note the change here rather than silently relabeling it agreed.
