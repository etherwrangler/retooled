# Agent House Rules

This fork welcomes AI-assisted work when it helps contributors understand the project,
plan changes, automate routine workflows, or verify behavior. The goal is to make the
project easier to maintain and learn from without outsourcing responsibility for the
codebase.

## Allowed Uses

Agents may be used for:

- Project planning, issue triage, architecture notes, and codebase orientation.
- Explaining existing Python, Qt, test, documentation, and packaging behavior.
- Suggesting implementation approaches for a human contributor to evaluate.
- Automating repeatable workflows, such as running formatters, checks, and test commands.
- Helping inspect test failures, compare outputs, and summarize diffs.
- Drafting or editing documentation, contributor notes, and release/process checklists.

## Boundaries

Agents should not be used to author production code or tests for this fork. They may help
explain how code works, identify likely areas to change, and assist a human contributor in
running or interpreting checks, but the contributor should write and own the actual code
and tests.

Agents must not invent clone relationships, metadata, Redump or No-Intro behavior,
compatibility claims, source evidence, changelog entries, or project history. Retool's
value depends on careful domain knowledge, reproducible behavior, and curated data.

## Contribution Expectations

Human contributors remain responsible for every submitted change, including any work that
was planned, reviewed, or checked with agent assistance.

Keep changes small, reviewable, and tied to a clear reason. Avoid broad rewrites,
format-only churn, or architectural changes without prior discussion.

Use Conventional Commits for commit messages. Prefer clear types such as `fix:`,
`feat:`, `docs:`, `test:`, `refactor:`, `build:`, and `chore:`. Mark breaking changes
explicitly with `!` or a `BREAKING CHANGE:` footer.

Use Semantic Versioning for releases. Version changes should communicate compatibility:
patch for compatible fixes, minor for compatible new functionality, and major for
breaking changes.

Update the changelog for contributor-facing changes. New entries should go in the
`Unreleased` section until a release is tagged.

Do not commit directly to `main`. Development should happen on short-lived branches, with
pull requests opened back to `main`. Treat `main` as the releasable branch and cut tagged
releases from commits that have landed there.

Respect the existing project shape:

- Core CLI flow starts in `retool.py`.
- GUI flow starts in `retoolgui.py`.
- DAT parsing lives under `modules/dat/`.
- Title selection lives under `modules/title_selection/`.
- Clone-list handling lives under `modules/clone_lists/`.
- Runtime data folders such as `config/`, `clonelists/`, `metadata/`, `mias/`, and
  `retroachievements/` are intentionally ignored and may be missing in a fresh checkout.
- Generated Qt/resource files should not be edited unless the task is specifically about
  the GUI generation workflow.

## Verification

Prefer focused verification for the area being changed. This project uses Hatch/uv,
Ruff, Black, isort, mypy, and script-style golden-file tests.

Tests may require runtime config and metadata files before they can run. If a check cannot
be run, say so clearly and explain what blocked it.
