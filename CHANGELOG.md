# Changelog

All notable changes to this project are documented here. Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/); versioning follows [SemVer](https://semver.org/).

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

[0.2.0]: https://github.com/robcsaszar/retrospective/releases/tag/v0.2.0
[0.1.0]: https://github.com/robcsaszar/retrospective/releases/tag/v0.1.0
