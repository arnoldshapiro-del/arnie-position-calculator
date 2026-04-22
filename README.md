# Arnie's Position Calculator v2

Standalone futures position-size and risk calculator tied to the Day Trading Setup Playbook v5.

## Modes
- **Forward** — enter stop distance and size -> get R, $ risk, targets
- **Reverse** — set the dollar risk, solve for max contracts
- **Fib** — target projection from swing points
- **EV** — expected value with win rate, avg W, avg L

## Instruments
MES, MNQ, M2K, ES, NQ, RTY — with per-instrument point-value and minimum stop buffers.

## Presets
Double Bottom, Double Top, Bull Flag, Bear Flag, Hammer, Failed Breakout — each loads stop buffer + scale-out defaults.

## Scale-out Default
- T1: 50% at 1.5R -> move stop to BE
- T2: 25% at 2.5R
- T3: 25% runner

## Features
- Saved plans (localStorage, persists across sessions)
- Keyboard shortcuts
- Mobile-friendly PWA
- Dark theme matching the Playbook

## Deployment
Static single-file HTML, React 18 + Babel via CDN. Auto-deployed from GitHub to Netlify.
