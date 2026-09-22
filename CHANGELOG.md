# Changelog

All notable changes to this project are documented here. Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/); versioning follows [SemVer](https://semver.org/).

## [0.3.0] - 2026-09-22

### Added

- **Step 4 — Contest the findings**, with `references/contest.md`. Every finding from Steps 2 and 3 is a hypothesis until it passes evidence (cite the moment), counter-evidence (find the moment that contradicts it; a rule founded on fewer than three moments is a hunch), and mechanism (would the fix have changed the cited moment, and does it conflict with a sibling skill's rule). Verdict per finding: confirmed, reframed, or falls — only survivors reach the Wiring section. A first pass here was two-of-seven wrong and missed the strongest item, which is what the step exists to catch.
- **Step 1 — "Was it seen?"**: before the score is final, list every user-facing surface the session changed and who looked at it — a capture, a run, a person, or nobody. A surface nobody looked at is a finding whatever the tests said.
- A **score cap of 6** for any session that shipped an unseen surface, overriding the scoring table in `references/shapes.md`. One session scored 7/10 on context economy alone and came back with nine defects from a single play.
- **Contested** section in the output — finding, verdict, and the moment it stood or fell on.

### Changed

- "Write the notes" renumbered Step 4 → Step 5; `Do NOT Load` updated to match.
- Step 2: magnitude stays relative *except* where the session's own tool output printed a number (a suite runtime, a `git log` count) — cite it, with its source.
- Step 3: an unseen surface gets its lever from the gate of the artifact that shipped it, never a note.
## [0.2.0] - 2026-09-01

### Added

- Environment levers reference (`references/environment-levers.md`): six named levers — navigation pointer, automated check, review-stage rule, steering trim, tool verbosity, information access — each with a use-when signal, its natural home file, and a severity ordering. Step 3 now asks "turn or ground?" for each badly-spent moment before asking what was done by hand around a called artifact, so a cost that would recur for any agent gets a fix at its source instead of a "be more careful" note.

### Changed

- Wire-in note gains a `lever` field and may target a steering file, a check config, a review-standards file, or a tool wrapper — not only a skill or workflow.
- Context-economy reference now routes ground-side costs (verbose-by-design tools, unreachable facts, hard-to-find files) to the levers rather than stretching a turn-side rule over them.
- Wiring output lists recommendations most severe first.
- Description names the lever concept so the router can tell this skill proposes environment fixes, not only skill edits.
- Eval suite moved from `skills/retrospective/evals/` to `evals/retrospective/` so the skill directory holds only `SKILL.md` and `references/`, per the Agent Skills spec.

## [0.1.0] - 2026-08-29

### Added

- Initial release: retrospective skill. Reviews how the current session was conducted from live context — classifies it against six session shapes with a 1–10 score key, accounts for where the context window was spent badly against five named economy rules, and turns repeatable hand-work into wire-in notes and skill briefs for the artifacts it used.

[0.3.0]: https://github.com/robcsaszar/retrospective/releases/tag/v0.3.0
[0.2.0]: https://github.com/robcsaszar/retrospective/releases/tag/v0.2.0
[0.1.0]: https://github.com/robcsaszar/retrospective/releases/tag/v0.1.0
