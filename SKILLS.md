# Base Skills — the recommended set

Skills are packaged abilities your assistant can trigger by name (a folder with a `SKILL.md`). This is the curated base set for a command center. You don't install all of them — during setup the assistant recommends the few that fit your work.

Three groups: **bundled** (ship in this folder, work everywhere), **built-in / one-click** (the official Anthropic skills — already available on paid Claude, installable elsewhere), and **command skills** (wire this system together).

---

## 1. Bundled with the kit (`.claude/skills/`)
Ready the moment you open the folder in Claude. Codex and other agents simply ignore them and fall back to the runbook.

| Skill | What it does | Why it's in the base set |
|---|---|---|
| `humanizer` | Rewrites AI-sounding text to read human and match *your* voice (from `core/identity.md`). | The single highest-leverage upgrade to how the assistant writes for you. |
| `command-center` | How the assistant should behave inside this workspace — apply your operating rules, use your voice, run the system verbs. | Makes the whole command center feel consistent. |
| `setup` · `add-tool` · `weekly-reflection` · `refresh-dashboard` | One-word triggers for the system's core actions. | Ergonomics — say "run my weekly reflection" and it just works. |

## 2. Built-in on paid Claude · one-click elsewhere
These are Anthropic's official skills (from [anthropics/skills](https://github.com/anthropics/skills), Apache-2.0 / source-available). On a paid Claude plan they're **already available** — just ask for them. In Claude Code: `/plugin marketplace add anthropics/skills`. We recommend, not copy them, so they stay current.

| Skill | Use it for | Recommend to… |
|---|---|---|
| `canvas-design` | Poster / magazine-quality visual art (PNG, PDF). | anyone making visuals, covers, one-pagers |
| `pptx` (slide decks) | Presentations and pitch decks. | anyone who pitches or teaches |
| `docx` · `pdf` · `xlsx` | Polished Word docs, PDFs, spreadsheets. | anyone producing documents or data |
| `frontend-design` | Distinctive, production-grade web UI (anti-"AI slop"). | anyone building sites, artifacts, the dashboard |
| `theme-factory` | 10 ready professional color themes. | pairs perfectly with the **dashboard** colors |
| `skill-creator` | Build and test your own skills. | once you want to extend the system |

## 3. Worth knowing (community)
| Skill | Use it for |
|---|---|
| Frontend / design skills (e.g. the popular `frontend-design`) | sharper interfaces than defaults |
| Writing-style / brand-voice skills | locking a consistent voice across everything |

---

## How the assistant uses this list
During setup (`START-HERE.md`, Step 3, Lane 3) the assistant reads your profile and recommends 1–2 skills from groups 2–3 that fit your work — a photographer gets `canvas-design`; a consultant gets `pptx` and `docx`. It tells you they're built-in (paid Claude) or how to add them, and never installs anything without you.

## Add your own
Drop any new skill into `.claude/skills/<name>/SKILL.md`. Minimal shape:
```
---
name: my-skill
description: What it does and when to use it.
---
# My Skill
Instructions the assistant follows when this skill is active.
```
