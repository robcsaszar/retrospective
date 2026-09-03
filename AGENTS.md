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

Releases are cut by the **Release** workflow (`.github/workflows/release.yml`), never by hand. It is a manual `workflow_dispatch` with one input, `tag`, and it releases the commit at the tip of the branch it is run on. Run it on `main`.

The workflow, in order:
1. Rejects a tag that is not `vX.Y.Z`, or that already exists.
2. Fails unless `version` in `.claude-plugin/plugin.json` and `plugins[0].version` in `.claude-plugin/marketplace.json` both equal `X.Y.Z`.
3. Takes the `## [X.Y.Z]` block from `CHANGELOG.md` as the release notes, and fails if there is none.
4. Creates the tag at the checked-out commit and publishes the GitHub release with those notes.

Nothing is created until every check passes, so a failed run leaves nothing to clean up.

To prepare a release, in one PR:
- Set the same new version in `.claude-plugin/plugin.json` and `.claude-plugin/marketplace.json`.
- Add a `## [X.Y.Z] - YYYY-MM-DD` block at the top of `CHANGELOG.md`, and its `[X.Y.Z]: …` link reference at the bottom.
- Merge to `main`.

Then run the workflow on `main` with `tag=vX.Y.Z`, from the Actions tab (**Release → Run workflow**) or from a shell:

```sh
gh workflow run release.yml --ref main -f tag=vX.Y.Z
```

Afterwards, confirm the release exists and its notes match the changelog block.

NEVER:
- Never push a tag or create a release outside the workflow. A hand-made tag makes the workflow refuse that version, and a hand-written release skips the changelog and version checks.
- Never work around a failed run by hand-writing notes or skipping a check. Fix the changelog or the manifests, merge, and re-run.
