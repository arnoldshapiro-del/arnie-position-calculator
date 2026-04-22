# Arnie's Position Calculator v2 — Standalone

## Project Name
Arnie's Position Calculator v2 — Standalone pre-trade command center for futures

## Purpose
A standalone single-file HTML app that replaces four separate calculator tabs inside the Playbook. Designed to be used BEFORE clicking buy — turns "is this trade big enough?" and "can I size into this?" from gut feel into a number. Also embedded as an iframe inside the Playbook's Calculators tab.

## GitHub Repo
`arnoldshapiro-del/arnie-position-calculator` (master branch)

## Netlify Site URL
https://arnie-position-calculator.netlify.app

## Tech Stack
- Single-file HTML + CSS + Vanilla JS
- React 18 UMD + Babel standalone via CDN (no build step)
- localStorage for saved plans (`arnie_calc_plan:` prefix)
- PWA: manifest.json, theme-color #d4a574 (warm gold)
- Firebase: NOT connected — no auth needed, not a private app

## Current Status
**v1.0 LIVE (2026-04-22).** First deployment. All 4 modes, 6 instruments, 6 presets, scale-out simulator, saved plans, keyboard shortcuts working.

## Modes
- **Forward** — enter stop distance + contract count → get R, $ risk, targets (T1/T2/T3)
- **Reverse** — set $ risk budget → solve for max contracts
- **Fib** — project targets from swing high/low using Fibonacci levels
- **EV** — expected value calculator (win rate × avg winner − loss rate × avg loser)

## Instruments + Stop Buffers
- MES: $5/pt, 1.0pt buffer
- MNQ: $2/pt, 1.5pt buffer
- M2K: $5/pt, 0.4pt buffer
- ES: $50/pt, 1.0pt buffer
- NQ: $20/pt, 2.0pt buffer
- RTY: $50/pt, 0.4pt buffer

## Pattern Presets
Double Bottom, Double Top, Bull Flag, Bear Flag, Hammer, Failed Breakout — each auto-loads stop buffer + scale-out T1/T2/T3 defaults.

## Scale-Out Default
T1 50% at 1.5R → move stop to BE · T2 25% at 2.5R · T3 25% runner

## Key Technical Note
The v5 Appendix in the Playbook (Final Trading Plan tab) contains a hyperlink to this URL: `https://arnie-position-calculator.netlify.app/`. That link is now live.

## Iframe Embedding Note
The app is embedded inside the Playbook at `arnie-double-top-bottom.netlify.app`. The `netlify.toml` uses `Content-Security-Policy: frame-ancestors` (NOT `X-Frame-Options: SAMEORIGIN`) to allow this embedding while preventing third-party embedding. Do NOT add X-Frame-Options back.

## File Structure
```
/
├── index.html      — Full single-file React app (~700 lines)
├── manifest.json   — PWA manifest (theme: #d4a574)
├── netlify.toml    — Static site config + CSP frame-ancestors header
├── README.md       — Repo readme
├── CLAUDE.md       — This file
└── SESSION_NOTES.md
```

## Project-Specific Rules
- Deploy via GitHub push → Netlify auto-builds
- Never add X-Frame-Options header (it would break the Playbook iframe embed)
- localStorage prefix `arnie_calc_plan:` — do not change or it breaks saved plans
