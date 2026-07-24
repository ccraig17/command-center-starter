---
name: refresh-dashboard
description: Rebuild the command-center dashboard so it reflects the latest files. Use when the user says "refresh my dashboard", "update my dashboard", or "rebuild my dashboard".
---

# Refresh Dashboard

Only relevant if the `dashboard` tool is on (check `tools/README.md`).

Read the current `core/` files, `tools/README.md`, and the contents of `workspace/` and `projects/`, then rebuild the dashboard per `tools/dashboard.md`:
- **Snapshot version:** regenerate `dashboard/dashboard.html` with the latest content, keeping the user's chosen colors, the arc reactor, and the boot sequence.
- **Live version:** the running server already reflects current files — just tell the user to reload the page.

Preserve the user's color choices — read them from the existing dashboard file rather than resetting to defaults.
