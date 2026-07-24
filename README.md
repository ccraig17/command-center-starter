# Your Command Center — Starter Kit

Turn any AI assistant (Claude or Codex) into a personal command center that knows who you are, what you're working toward, and how you like to work — so you stop re-explaining yourself every time.

You don't need to be a developer. You don't need to edit any files yourself. The assistant sets everything up by interviewing you.

---

## 1. Get the folder

### If you're not a developer (easiest)
1. Click the green **Code** button at the top of this page → **Download ZIP**.
2. **Unzip** it (double-click the downloaded file).
3. **Rename** the folder to whatever you want to call your command center — for example `my-command-center`. This becomes your personal workspace.
4. **Move** it wherever you keep your things (Documents, Desktop, anywhere you'll find it).

### If you're a developer
Fork or clone it instead:
```bash
git clone https://github.com/<your-username>/command-center-starter.git my-command-center
```
Using **git** is a nice-to-have, not a requirement — if you're comfortable with it, it gives you version history and easy backups of your command center as it grows. If that means nothing to you, ignore this and use the download steps above.

---

## 2. Open it and start

1. **Open the folder as a project** in Claude (Cowork or Claude Code) or in Codex.
2. **Run this prompt** to kick off the setup:

   > **Read START-HERE.md and set up my command center.**

3. **Answer the questions** it asks. That's it — about 5 minutes.

The assistant creates your personal files as you talk, then recommends a few "tools" you can switch on (a calendar helper, a content helper, a weekly reflection, and more) based on what you tell it.

---

## What you'll end up with

```
my-command-center/
  CLAUDE.md          ← the "brain" — loads everything below automatically
  core/              ← who you are + how the assistant thinks
    identity.md      ← who you are, in your words
    goals.md         ← what you're working toward right now
    hot.md           ← your current focus (changes often)
    operating-rules.md ← how you want the assistant to think and respond
  tools/             ← optional add-ons you switch on when you want them
  workspace/         ← where your day-to-day work lands (drafts, notes, ideas)
  projects/          ← bigger, longer-running efforts, each in its own folder
```

Nothing is permanent. You can re-run the interview anytime, edit anything, or ask the assistant to change how it works.

## The four layers (so you know what's happening)

1. **The engine** — the reusable "how to think" rules. You never touch these.
2. **You** — your identity, goals, and focus. Built from the interview.
3. **Tools** — capabilities you add over time. Start with one, add more when ready.
4. **Your stuff** — `workspace/` for everyday work, `projects/` for the big efforts.

During setup the assistant also recommends **connectors** (live links to apps you already use — calendar, email, notes) and **skills** (installable helpers). A few skills come ready in the box, so in Claude you can just say things like "run my weekly reflection" or "refresh my dashboard" from day one.

There's also an optional **dashboard** — a visual "JARVIS" home screen for all of this, in colors you choose, with an animated arc-reactor and boot-up. It starts as an instant snapshot (nothing to install); a full self-updating version is available later if you want it. It's the one advanced extra — leave it for last.

Start small. One tool working beats ten half-built ones.
