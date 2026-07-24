# Tool: Dashboard (advanced)

**What it does:** Turns your command center into a visual home page — a "JARVIS"-style control screen showing your current focus, goals, what needs attention, your tools, and recent work at a glance. This is the one advanced tool. There is **no pre-built dashboard shipped** with this kit — you (the assistant) build one for the user, tailored to them, using the design spec below.

---

## Step 1 — Help the user decide (don't build yet)

The dashboard is optional and it's the *last* thing to add, not the first. Only bring it up once the user has their core files and at least one other tool working. Then help them decide honestly:

**It's worth building if the user says yes to most of these:**
- "I'd actually open a home screen for this each day."
- "I have data that changes — a calendar, content stats, opportunities, a task list — that I'd want to see live."
- "Seeing everything in one place would help me focus or feel in control."

**Skip it (for now) if:**
- They're happy just talking to the assistant and opening files.
- Nothing in their setup changes day to day (a static dashboard adds nothing).
- They'd never actually look at it. A dashboard nobody opens is pure overhead — the bloat filter applies.

If they're unsure, offer the **snapshot** version first (Step 2A). It's a 10-second win with no commitment. Only build the live version (Step 2B) if they want something that updates itself.

---

## Step 2 — Build it (JARVIS-style, in their colors)

Whichever version, follow the **look & feel spec** further down so it feels like a real command center, not a plain webpage. Personalize it: use the user's name in the title (e.g. `NADIA // COMMAND CENTER`), never a generic label.

### Step 2.1 — Let the user choose the colors
The JARVIS structure stays the same; the accent colors are theirs. Ask what vibe they want and recommend a fit — don't just impose one. Offer these presets and let them pick, tweak, or go custom:

| Preset | Base | Accents | Feels like |
|---|---|---|---|
| **Signal** (the classic) | near-black `#05070a` | orange `#ff7a1a` + cyan `#28c8ff` | Iron Man HUD, warm + techy |
| **Mint Terminal** | black `#04080a` | green `#39d98a` + teal `#28c8ff` | hacker console, calm focus |
| **Synthwave** | deep indigo `#0b0713` | magenta `#ff4dd8` + violet `#a06bff` | retro-future, high energy |
| **Arctic** | slate `#0d1117` | ice-blue `#4aa8ff` + white | clean, minimal, corporate-cool |
| **Ember** | charcoal `#0a0808` | red `#ff5b5b` + amber `#ffcf4a` | intense, alert, high-contrast |
| **Custom** | ask for a base + two accents | — | fully theirs |

Recommendation logic: match the accent to their work and personality — calm/creative → Mint or Arctic; bold/creator → Signal or Synthwave; operator/serious → Ember or Arctic. Suggest one, but the choice is theirs. Keep the near-black base and the glow/grid atmosphere for all of them — that's what makes it read as a command center rather than a website. Store the chosen colors as CSS variables at the top so they can be changed in one place later.

### Step 2.2 — Include the default widgets (so it's never empty)
Even before the user adds tools, the dashboard must feel alive out of the box. Always include these **system widgets**, built from the core files that always exist:

- **Live clock + date** and a **greeting line** ("Good morning, {{NAME}}") in the navbar.
- **★ Right Now** — the one thing that matters + capacity, from `core/hot.md`.
- **Goals** — from `core/goals.md`.
- **Focus timer** — a simple start/stop focus (pomodoro-style) block; a satisfying default that needs no data.
- **System Status** — which tools are on/off, from `tools/README.md` (shows "all systems nominal" energy even with nothing enabled yet).
- **Today / Quick Note** — a small panel for a jotted intention or note.

As the user switches tools on, their panels (calendar, content, opportunities…) join this baseline. But the six above are always present, so a brand-new dashboard already looks and feels complete.

> **The "first look" during onboarding.** The setup runbook (`START-HERE.md`) may call for a quick snapshot right after the core files are written — before any tools are on. That's fine and encouraged: build the snapshot with exactly these six default widgets (System Status will show everything "off"). It's the mid-setup payoff — proof the command center already knows the user. Full boot sequence and arc reactor included; that's what makes the moment land.

> **Build from the canonical reference — this is how output stays consistent for everyone.** Don't design a dashboard from scratch. Start from `tools/dashboard-reference.html`, which is the locked skeleton (arc reactor, boot sequence, layout, fonts, animations already built). Copy it, replace the `{{TOKENS}}` with the user's data, swap the two accent colors, and save the result. Never restructure or restyle it — only inject data and colors. The token list is at the bottom of that file. The design spec below explains *why* it looks the way it does; the reference file is *what you build from*.

### Step 2A — Snapshot (default, nothing to install)
1. Read `core/identity.md`, `core/goals.md`, `core/hot.md`, `tools/README.md`, and list `workspace/` and `projects/`.
2. Copy `tools/dashboard-reference.html`, fill in every `{{TOKEN}}`, and set `{{ACCENT_1}}`/`{{ACCENT_2}}` to their chosen colors. All CSS is already inline; the only external load is Google Fonts.
3. Save the filled copy as `dashboard/dashboard.html` (leave the reference untouched). **Delete the two guide comments** — the `CC-REFERENCE` line at the top and the token-list block at the very bottom — so the user's file is clean. Then tell them to double-click it to open.
4. It's a snapshot — it shows the moment you made it. When they say "refresh my dashboard," rebuild it from the reference again. To keep it current automatically, set up a scheduled refresh (Step 3).

> If you're running in Cowork, you may instead build this as a live artifact that refreshes when opened — use that if available; it's the smoothest version of the snapshot.

### Step 2B — Live local app (self-updating)
A tiny local program that reads the user's files fresh on every page load, so it's always current.
1. Build a small **zero-dependency Node server** (built-in `http` + `fs` only — no `npm install`). It reads the `core/` files, `tools/README.md`, and lists `workspace/`/`projects/` on each request and renders **the same markup as `tools/dashboard-reference.html`** (same arc reactor, boot, layout — just populated live). Serve on a local port (e.g. 4321).
2. Include a `package.json` with a `"start": "node server.js"` script for convenience.
3. **If you have a shell** (Cowork or Claude Code): check `node --version`, install Node if missing, start the server yourself, and hand the user the link (http://localhost:4321). Do the work — don't make a non-developer type commands.
4. **If you don't have a shell:** walk them through it slowly — install Node from nodejs.org (the "LTS" button), open a terminal, `cd` into the dashboard folder, run `node server.js`, open the link. Check in after each step. Never assume they know what a terminal is.
5. If anything fails, fall back to the snapshot (2A) so they still get a win.

---

## Step 3 — Keep the data fresh (scheduling)

A dashboard is only as alive as the files behind it. The live server always reflects the *current* files — so "keeping it updated" really means **refreshing the source data on a schedule.** Set this up so the user never has to.

1. Identify what should refresh and how often, based on their active tools:
   - `calendar` → pull today's events each morning.
   - `content` → refresh stats/metrics daily (needs a connector).
   - `opportunities` → run a scan weekly.
   - `weekly-reflection` → prompt once a week; it updates `core/hot.md`.
2. Set it up as a **scheduled task**. In Claude (Cowork or Claude Code), create a Claude scheduled task — e.g. a daily task at 7am with a prompt like *"Refresh my command center: update today's calendar, refresh content stats, and rebuild the dashboard."* The task runs on its own and updates the files (and, for the snapshot version, rebuilds `dashboard/dashboard.html`).
   - **If the user is on a different agent** (Codex or another tool): tell them to check how scheduled/automated tasks work for *that* agent and set the same prompt on its scheduler. The concept is identical — a saved prompt that runs on a cadence — only the setup screen differs.
   - **Terminal-comfortable users only:** a cron job calling the refresh is an option, but the built-in scheduled task is the non-developer path — prefer it.
3. Tell the user in plain language what you set up: *"Every morning I'll refresh your dashboard so it's current when you open it."* Confirm the time with them.

Keep cadence honest: don't schedule refreshes for data that doesn't change. Daily for calendar/stats, weekly for opportunities/reflection is plenty.

---

## Look & feel spec — the JARVIS command-center aesthetic

Build every version to this spec so it feels like a heads-up display, not a document.

**Fonts (via Google Fonts):**
- `Orbitron` (700/900) — the logo, the clock, big numeric readouts. Wide letter-spacing.
- `JetBrains Mono` — panel labels, data rows, timestamps, anything "system".
- `Space Grotesk` — body text and longer content.

**Palette — user-chosen accents on a near-black base.** The two accent colors come from the user's pick in Step 2.1. The base, text, and status colors below stay roughly constant across presets (nudge the base tint to match the theme — e.g. slightly indigo for Synthwave). Define everything as CSS variables at the top so a color change is a one-line edit.
```
--bg:     #05070a     /* near-black base — tint to taste per preset  */
--bg2:    #0a0e13     /* raised background                           */
--card:   #0e1218     /* panel base                                  */
--line:   #1b2431     /* hairline borders                            */
--fg:     #dfe7ee     /* primary text                                */
--muted:  #69788a     /* secondary text / labels                     */
--accent:  {{ACCENT_1}}   /* the user's primary accent — focus, highlights */
--accent2: {{ACCENT_2}}   /* the user's secondary accent — labels, links, meters */
--ok: #39d98a   --warn: #ffcf4a   --err: #ff5b5b     /* status (keep) */
```
The default reference ("Signal" preset) is orange `#ff7a1a` + cyan `#28c8ff` — use it only if the user has no preference.

**Atmosphere (this is what sells the JARVIS feel):**
- **Arc reactor (the signature element — required, don't skip it):** a small animated arc-reactor mark sits in the navbar as the logo. Build it in SVG: **3+ concentric rings that counter-rotate** at different speeds (e.g. outer 14s, mid 9s, inner 6s-reverse), a set of accent nodes on the outer ring, and a **pulsing white core** with a soft glowing halo behind it (scale + opacity pulse, ~2.4s). Both accent colors appear in the rings. This is the one element people screenshot — make it unmistakable, not a faint spinning dot.
- **Boot sequence on load (required):** a full-screen overlay that plays for ~2.5s then fades to reveal the HUD. Center a large version of the arc reactor with 1–2 expanding "ping" rings radiating out, a mono line reading `Initializing {{NAME}} // Command Center`, and a thin load bar that fills. Then the panels rise/fade in, staggered by column. This is the moment that makes it feel alive — and it's the hero shot for any demo or video.
- A fixed background layer (`body::before`) combining faint **radial glow** pools (accent-1 top-center, accent-2 bottom-right, ~5–7% opacity) over a subtle **grid** (1px lines every ~38px at ~2% white).
- **Panels:** translucent dark gradient, 1px `--line` border, 12px radius, `backdrop-filter: blur(5px)`. Each has a header row — a small accent-2 uppercase mono label with wide letter-spacing — above its body.
- **Glow accents:** accent `text-shadow` on the logo and clock; status dots with a matching `box-shadow` glow.
- **Motion, tasteful:** panels fade/slide in after the boot; a live ticking clock; the reactor always turning. A hum, not a light show — but the reactor and boot are the parts that must land.

**Layout:**
- Top **navbar** (~60px): the arc-reactor mark + `NAME // COMMAND CENTER` in Orbitron, a mono greeting/status line, and a live clock + date on the right.
- Main **HUD grid**, three columns (roughly `300px | 1fr | 320px`), each a scrollable stack of panels. Suggested panels:
  - **★ Right Now** (highlighted, orange border) — from `core/hot.md`: the one thing that matters + capacity.
  - **Goals** — from `core/goals.md`.
  - **Needs Attention / Next Actions** — the highest-leverage moves, with severity dots.
  - **Tools** — active tools and their status, from `tools/README.md`.
  - **Workspace** — recent items from `workspace/`.
  - **Projects** — from `projects/`.
- Responsive: collapse to a single column on narrow screens.

**Tone of the copy on screen:** terse, system-like, confident. Mono labels in uppercase (`FOCUS`, `PRIORITY QUEUE`, `SYSTEM STATUS`). It should read like a console that respects the user's attention.

---

## Guardrails
- Always offer the snapshot first. Only build the live server if the user specifically wants self-updating.
- The dashboard is **read-only** — it displays files, never edits them.
- Don't over-schedule. Refresh only what actually changes.
- If the live build stalls, fall back to the snapshot so the user still ends with something on screen.

## When switched on
Create a `dashboard/` folder in the user's command center, build the version they chose into it, set up the refresh schedule, then mark this tool **on** in `tools/README.md`.

---
*Mark this tool **on** in `tools/README.md` once set up.*
