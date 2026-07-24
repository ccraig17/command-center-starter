# Tool: Weekly Reflection

**What it does:** A short weekly check-in that reviews the past week against your goals, updates your current focus, and sets the one thing that matters most next week. This is the habit that keeps the whole command center alive — without it, `core/hot.md` goes stale and the assistant slowly stops being useful.

## Setup (ask the user)
1. What day and time works for your check-in? (default: Friday afternoon or Sunday evening)
2. Do you want me to run it automatically on a schedule, or wait for you to say "run my weekly reflection"?

If they want it scheduled and the assistant supports scheduled tasks, offer to set that up. Otherwise, just remember the cadence.

## How to run it
Keep it to ~5 minutes. Ask, one at a time:
1. What actually moved forward this week? (wins, however small)
2. What stalled or drained you?
3. Given that — what's the ONE thing that matters most next week?

Then:
- Update `core/hot.md` with the new "one thing that matters most" and anything that changed in capacity.
- If a goal in `core/goals.md` is done or no longer relevant, update it.
- End with one specific next action for the week ahead. One, not a list.

## Keep it honest
Don't let it become a status-report ritual. If the same thing has stalled three weeks running, say so plainly and help them either commit to it or drop it.

---
*Mark this tool **on** in `tools/README.md` once set up.*
