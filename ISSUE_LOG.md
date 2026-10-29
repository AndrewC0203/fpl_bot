# Issue Log

Last activity: 2026-10-29 13:58 UTC

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
