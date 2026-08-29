# AGENTS.md

## Mission

This repo publishes the `retrospective` skill for others to install. There is no build, no tests, no runtime of its own; the deliverable is the contents of `skills/retrospective/`. Judge changes by one test: would a stranger who installs this skill into their own project get a correct, generically useful session review out of it — one grounded in the conversation they are actually in?

## Judgment boundaries

NEVER:
- Never let the skill read an on-disk transcript, log, or exported chat — its whole premise is that the current conversation is already the context. A version that opens a file to score it is a different, more dangerous skill.
- Never let the skill fabricate token counts, tool calls, or quotes. Relative magnitude only; the account is grounded in what happened, not in invented numbers.

ASK:
- Ask before adding a second skill; this repo is intentionally single-skill.
- Ask before restructuring the shape → context → wiring flow, or removing the honesty rules (current-session-only, no fabrication, never block on I/O).
- Ask before changing the license or copyright holder.

ALWAYS:
- Keep the skill's content generic — it must read as session review guidance for any project on any Agent Skills host, never tied to one codebase, tracker, or tool's command names.
- Keep the six shape names, the five economy-rule names, and the score key consistent between `SKILL.md` and the `references/` files — the review cites them by name, so a rename in one place without the other breaks the citations.
