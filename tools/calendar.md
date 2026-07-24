# Tool: Calendar & Daily Prep

**What it does:** Helps you start each day ready — a quick brief of what's ahead, conflicts flagged, and focus time protected against your goals.

## Setup (ask the user)
1. Which calendar do you use? (Google, Outlook, Apple, other)
2. Do you want a daily morning brief, or just help when you ask?
3. What time does your day usually start?

## Connect the calendar
This tool is far more useful with a live connection. Check whether the user's assistant has a calendar connector available:
- If yes, guide them to connect it in their assistant's integration/connector settings, then read real events.
- If no connector is available, the user can paste their day's schedule and you work from that.

Do not attempt to handle logins or authentication tokens yourself — point them to the settings and let them connect.

## How to run the daily brief
When asked (or on schedule), produce a short brief:
- Today's meetings, in order, with any prep needed for each.
- Conflicts or back-to-backs flagged.
- The one block of focus time to protect for the user's top goal (`core/hot.md`).
- One line: the single most important thing to get done today.

Keep it scannable. No walls of text.

## Guardrails
- Never create, move, or cancel events without explicit confirmation.
- Protect capacity: if the day is overbooked relative to `core/hot.md`, say so.

---
*Mark this tool **on** in `tools/README.md` once set up.*
