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

## Releasing

A release is one workflow run, never a hand-pushed tag or a release written in the GitHub UI — that is what keeps the release notes identical to the changelog.

WHEN:
- After a version-bump PR has merged to `main`. The bump is complete only when three places agree on the new version: the top `## [x.y.z] - date` heading in `CHANGELOG.md`, `version` in `.claude-plugin/plugin.json`, and `plugins[0].version` in `.claude-plugin/marketplace.json`. Add the `[x.y.z]: …/releases/tag/vx.y.z` link reference at the bottom of the changelog in the same PR.

HOW:
- Dispatch `.github/workflows/release.yml` on `main` with `tag=vx.y.z` and `target=<merge commit of the bump PR>` (defaults to `main`; pass the SHA when later commits have landed so the tag excludes them).
- The workflow checks out the target, takes the matching `## [x.y.z]` block from `CHANGELOG.md` as the notes, creates the tag at the target if it does not exist, and publishes the release. It fails when the changelog has no block for that version — fix the changelog and re-run; never hand it notes another way.
- Verify afterwards: the tag resolves to the intended commit and the release body matches the changelog block.

NOT COVERED:
- The GitHub About sentence. It is a repository setting no workflow token can change; set it by hand to the `description` in `plugin.json` whenever that value changes.
- Pushing tags from a remote agent session. The proxy refuses tag pushes and release API calls, which is why the workflow exists — dispatch it instead of retrying.
