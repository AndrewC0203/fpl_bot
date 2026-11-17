# Issue Log

Last activity: 2026-11-12 15:44 UTC

## ISSUE-1
- Date logged: 2026-10-27
- Location: frontend/src/App.css, line 1
- What is wrong: the `@import "tailwindcss"` statement has no terminating semicolon, so the CSS parser reads the following rule as part of the import and reports "media query expected".
- Status: fixed
- Asks this session: 0

## ISSUE-2
- Date logged: 2026-10-29
- Location: frontend/tsconfig.json, `compilerOptions` (lines 7-13)
- What is wrong: this root tsconfig is a solution-style file (`"files": []` plus `references`), and `compilerOptions` in it are not inherited by the referenced projects. The `@/*` alias is therefore not applied to `tsconfig.app.json`, which is the project that type-checks `src`. Separately, `"@/*": ["./*"]` maps to the `frontend` root rather than `src`.
- Status: open
- Asks this session: 0

## ISSUE-3
- Date logged: 2026-10-29
- Location: frontend/vite.config.ts
- What is wrong: no `resolve.alias` for `@`, so Vite cannot resolve `@/...` imports at build time. The `@tailwindcss/vite` plugin is also installed but not registered in `plugins`, so Tailwind is not processed.
- Status: open
- Asks this session: 0

## ISSUE-4
- Date logged: 2026-11-10
- Location: DB schema design (stated in Claude Code chat, 2026-11-10): Players table primary key (id, week) combined with element-summary `history` rows stored in Players
- What is wrong: `history` is per match (each row has its own `fixture`). In a double gameweek a player has two `history` rows with the same `round`, so both map to the same (id, week) key and cannot both be stored. Not yet observed this season (no double gameweek in GWs 1-10).
- Status: open
- Asks this session: 0

## ISSUE-5
- Date logged: 2026-11-10
- Location: DB schema design (stated in Claude Code chat, 2026-11-10): rule that the week for bootstrap-static data is the event with `is_current` true
- What is wrong: before the GW1 deadline passes (pre-season), no event has `is_current` true, so bootstrap-static data has no week to be stored under. Based on known FPL API behaviour, not observed in this session's data.
- Status: open
- Asks this session: 0
