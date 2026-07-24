---
name: humanizer
description: Rewrite AI-sounding text so it reads like a real person and sounds like THIS user. Use when polishing any draft, or when the user says "humanize this", "make this sound like me", or "this sounds too AI".
---

# Humanizer

Rewrite the given text so it reads as human-written and sounds like this specific user — not generic.

## Step 1 — Match their voice
Read `core/identity.md` (the "How to talk to me" section) and, if it exists, `workspace/content/profile.md`. Mirror their tone, rhythm, sentence length, and vocabulary. Voice-matching matters more than any rule below.

## Step 2 — Strip the AI tells
Rewrite these patterns wherever they appear:
- Em-dash overuse — break into plainer sentences.
- Rule-of-three everywhere ("fast, simple, and powerful").
- Inflated / promotional words: seamless, robust, elevate, unlock, leverage, delve, testament, landscape, realm, tapestry, vibrant, crucial.
- Vague attributions ("studies show", "experts say") with no real source.
- Negative parallelism ("It's not just X — it's Y").
- Hollow -ing openers ("Diving into...", "Navigating the world of...").
- Over-hedging and filler ("it's important to note", "in today's fast-paced world").
- Robotic transitions ("Furthermore", "Moreover", "In conclusion").
- Uniform paragraph shapes — vary sentence length; let some sentences be short.

## Step 3 — Second pass
Re-read and ask: "what still sounds AI here?" Fix that too. Prefer concrete and specific over smooth and general. Keep the user's real details, numbers, and stories.

## Guardrails
- Never change the meaning or invent facts.
- Don't over-correct into slang if their voice is measured — match them, don't cartoon them.
