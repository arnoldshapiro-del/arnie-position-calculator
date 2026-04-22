# Session Notes — Arnie's Position Calculator v2

## Session — 2026-04-22 — v1.0 Initial deployment

**What we did:**
- Created standalone single-file HTML app from `position-calculator-v2.jsx` source file on Arnie's Desktop.
- Converted React JSX component (787 lines) to run in-browser via React 18 UMD + Babel standalone CDN — no build step required.
- Replaced Anthropic sandbox `window.storage` API with localStorage (`arnie_calc_plan:` prefix) for real persistent plan storage.
- Added PWA meta tags: manifest.json (theme-color #d4a574), apple-mobile-web-app-capable, inline SVG favicon.
- Created GitHub repo `arnoldshapiro-del/arnie-position-calculator` and pushed.
- Connected to Netlify with two-way GitHub sync (installation_id 77160536).
- **Bug:** Initial netlify.toml had `X-Frame-Options: SAMEORIGIN` which blocked the app from loading inside the Playbook's iframe. Fixed by replacing with `Content-Security-Policy: frame-ancestors 'self' https://arnie-double-top-bottom.netlify.app https://*.netlify.app`.
- Created .url shortcut: `Arnie's Position Calculator v2.url` in `All Of My Working Apps That Are Beautiful\`.
- Added gallery card + Puppeteer screenshot to arnies-app-showcase.

**What's working:**
- All 4 modes (forward/reverse/Fib/EV) functional
- All 6 instruments with correct point values and stop buffers
- All 6 pattern presets (Double Bottom/Top, Bull/Bear Flag, Hammer, Failed Breakout)
- Scale-out simulator (T1 50% 1.5R, T2 25% 2.5R, T3 25% runner)
- Saved plans via localStorage
- Keyboard shortcuts
- Embedded correctly in Playbook Calculators tab (iframe works)
- Live at https://arnie-position-calculator.netlify.app

**What's next:**
- No immediate work needed
- Could add Firebase auth lockdown if Arnie wants it private
- Could add more instruments or presets on request

**Important decisions:**
- Used `frame-ancestors` CSP instead of removing X-Frame-Options entirely — allows Playbook embed while preventing random third-party embeds
- localStorage over `window.storage` — localStorage is permanent and doesn't require Anthropic sandbox environment
- Warm gold theme (#d4a574) to visually distinguish from the Playbook's teal theme

**Problems encountered:**
- First load showed "Site not found" — Netlify build hadn't propagated yet when Arnie opened it
- Second attempt showed "refused to connect" — X-Frame-Options was blocking the iframe. Root cause identified immediately from browser error message. Fixed in one edit.
