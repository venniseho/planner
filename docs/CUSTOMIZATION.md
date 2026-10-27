# Appearance vision and staged implementation

**Product direction (user-requested):** multiple color themes, aesthetic preset themes, and user-customizable colors/presets. Avoid cloning other products' artwork or theme assets.

## Theme types

| Mode | Intended behavior | Stage |
|---|---|---|
| Base light / dark | Readable foundational variants | Phase 1 |
| Color palettes | Rainbow families **red, orange, yellow, green, blue, indigo, violet**, plus pastel variations | Product goal; starter set in M5 |
| Aesthetic presets | Coordinated color + font: **Green Botanist, Light Academia, Dark Academia, Starry Night** | Curated library in later spec |
| Custom colors | Edit and save own color palette | Later editor spec |
| Custom presets | Save named combined colors + fonts | Later editor spec |

## Typography candidates

| Style | Suggested font | Status |
|---|---|---|
| Modern friendly sans | DM Sans | Requested |
| Distinctive geometric sans | Space Grotesk | Proposed |
| Elegant serif | Cormorant Garamond | Proposed |
| Typewriter-like serif | Courier Prime | Proposed |
| Code / monospace | JetBrains Mono | Proposed |

All fonts are proposals pending licensing, character-set, legibility, performance, and offline caching review. A font selector should not force a preset's palette to change; selecting a preset may set palette and typography together, with optional later overrides.

## Guardrails

- Design tokens drive surfaces, borders, text, accent and focus; no duplicated component-specific hard-coded palettes.
- Status-only semantic badges/flags (overdue, due today, completed) use status colors; task background remains themed.
- Check contrast in both light/dark and themed variants, including keyboard focus.
- Save preferences locally in Phase 1; cloud account preference syncing is Phase 2+.
- M5 is an **initial selector and token foundation**, not a commitment to deliver every preset/editor listed above.
