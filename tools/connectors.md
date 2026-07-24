# Tool: Connectors

**What it does:** Connects your assistant to the real apps you use — calendar, email, notes, tasks — so it works with your actual data instead of what you paste in.

## What a connector is (plain version)
A connector is a secure link between your AI assistant and an app you already use. Once connected, the assistant can read (and sometimes update) that app on your behalf. You approve the connection; you can revoke it anytime.

## Setup (ask the user, then guide)
1. Which apps do you most want connected? (calendar, email, notes like Notion, tasks like Todoist, chat like Slack…)
2. For each, check whether the user's assistant offers that connector:
   - **Claude:** connectors are managed in settings / the connector directory.
   - **Codex / other:** check that tool's integrations settings.
3. Guide the user to connect it there. Do **not** ask for passwords, tokens, or login codes yourself — connection always happens in the app's own settings.

## Common starting connectors
| You use… | Look for a connector for… | Pairs well with tool |
|---|---|---|
| Google/Outlook/Apple Calendar | Calendar | `calendar` |
| Gmail/Outlook | Email | — |
| Notion / notes app | Notes/docs | `content`, `weekly-reflection` |
| Todoist / Things / tasks | Tasks | `weekly-reflection` |
| Slack / Teams | Chat | — |

## After connecting
Confirm it worked by reading one small thing (e.g. today's calendar) and showing the user. Then note which connectors are live so other tools can use them.

## Guardrails
- Read freely; never send, delete, move money, or make irreversible changes without explicit confirmation.
- If a connector isn't available, the tool still works — the user just pastes the data manually.

---
*Mark this tool **on** in `tools/README.md` once set up.*
