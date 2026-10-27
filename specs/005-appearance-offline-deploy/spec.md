# M5 — Customization foundation, offline shell, export and deployment

**Status:** Draft; human review required before implementation. **Sequence:** after earlier milestone validation.

## Goal

Provide a coherent customizable local-first application that works offline and can be hosted free-tier-first.

## In scope

- Implement semantic theme tokens and independent `palette_id`/`font_id` settings with a preset selection layer; no per-card recoloring for status.
- Offer functional light/dark themes and an approved starter subset of pastel/rainbow color palettes and typography options; final Phase 1 list set during human visual review.
- Target font roster (pending font license/asset checks): DM Sans, Cormorant Garamond (elegant serif), Courier Prime (typewriter), JetBrains Mono (code-like), Space Grotesk (contrasting sans).
- Product vision includes original aesthetic presets (Green Botanist, Light Academia, Dark Academia, Starry Night), customizable palettes and saved custom palette+font presets; full library/editor deferred to new specs, not an M5 acceptance promise.
- Persist preferences locally, work without external font-network access after offline assets are cached, maintain accessible text/background contrast and visible keyboard focus.
- Add installable PWA shell and verified offline asset caching, local task-data export, and frontend-only Cloudflare deployment via GitHub; do not deploy the FastAPI scaffold.

## Acceptance criteria

1. Selected starter theme/font survives refresh and offline app reopening; task card surfaces preserve theme even when badges are red/amber/green.
2. Offline app shell and saved tasks accessible in tested supported browser conditions; document browser-storage risks.
3. Export produces portable local records and is verified readable on test data; do not call export a full restore unless import exists.
4. Live frontend URL and deployment steps recorded only after actual deployment and review; no cloud-sync claims.

## Not in scope

- Cloud authentication/sync, custom remote APIs, Pomodoro, gamification and calendar integration unless separately specified.
- Unrequested helpers, parallel implementations, or speculative migration layers.

## Engineering / handoff

Implement as a small Spec Kit/Codex slice, not the whole milestone at once. Respect root `AGENTS.md`, existing files, typed functions, tests and human validation. After verification update `docs/PROGRESS.md`, relevant decision docs, and README; remove obsolete code only after approval.
