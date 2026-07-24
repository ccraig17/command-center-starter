---
name: add-tool
description: Switch on a command-center tool. Use when the user says "add a tool", "set up my calendar/content/opportunities tool", "turn on the dashboard", or asks for a new capability.
---

# Add a Tool

Read `tools/README.md` to see what's available and what's already on. If the user named a tool, open its file in `tools/`; if not, recommend the 1-2 best fits based on `core/` and ask which they want.

Then follow that tool's setup: ask its 1-2 setup questions, create its `workspace/<tool>/` folder if it produces work, connect any connector it needs (point the user to their assistant's settings - never handle logins yourself), and mark it **on** in `tools/README.md`.

Do one tool at a time. If the dashboard is on, offer to refresh it so the new tool shows up.
