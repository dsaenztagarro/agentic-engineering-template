# Changelog

All notable changes to this project are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.3.0] - 2026-10-05

### Added

- **A `design-repo` skill** that creates a design repository — a product's design or a shared design system — from one skeleton: the root files, `briefs/README.md`, the weekly CI, a `Rakefile` whose `rake` is the gate, and a `bin/sync` for either export kind that refuses an export of the wrong kind, a page that is not one canonical prototype per surface, and an edit to a file the repository authors upstream, with a test for each. It also adopts the layout check in an existing repository.
- **A layout check for design repositories**, `test/layout_test.rb` in the `design-repo` skill's skeleton: each design repository copies it into its own `test/`, so `rake` fails when the repository leaves the layout — an unnamed root entry, a symlink, an ignored part of an export, a request queue inside an export, a misnamed brief or vendored system, a `CLAUDE.md` that is not an import, scratch left trackable.

## [0.2.0] - 2026-10-05

### Changed

- **Renamed to `agentic-engineering-template`.** "AI engineering" names building applications on language models; this template is about engineering *with* agents.
- **Every corpus an agent reads is bounded.** Decision records move to `docs/adr/`: a few broad themes, one record each, named for the theme and amended in place, with superseded reasoning on a per-theme decision-log issue. `/epic` amends themes once, at close-out, instead of writing a record per ticket. `docs/adr/decision-records.md` records why.
- **Design content moves to a sibling `<project>-ds` repository**, with one generated artefact crossing. The `design-handoff` skill is the procedure, including the three routes into a Claude Design project.

- **Each ticket gets its own worktree**, `claude --worktree issue-<N>` under a git-ignored `.claude/worktrees/`, so two agents never share a checkout and the same name re-enters it.

### Added

- **A `brief-closer` agent**, which closes a brief once its surface ships and verifies each ask before deleting anything.
- **A `design-handoff` skill**, the Claude Design procedure an agent follows when it writes a brief or reads an export back. It rules that a page draws the surface — every state, interaction included — and never the application's behaviour, a rule seeded into the design project's own `readme.md`; names a design project for its codebase and a shared design system for its brand, never its platform; lands a component the shared system lacks through one byte-identical stand-in and a brief in the shared system's own repository, deleted when the component ships; and states in `layout.md` the one layout every design repository keeps, folder by folder — a product's design and a shared design system alike.
- **README §10 lists the skills the workflow uses**: the ones shipped here, the ones each project creates (`read-designs`, `design-curator`), and the user-level ones created once for every project (`tracker-plan`, `tracker-resume`, `tracker-pause`, `tracker-close`, `deps-upgrade`, knowledge capture), with the phase of the work each carries.

### Removed

- **`docs/features/`, `docs/specs/`, `docs/guides/`, `docs/architecture/` and `docs/designs/`.** Each grew one file per feature, decision or brief. Behaviour is stated by tests, the reasoning by themed records, commands by the README and procedures by skills; nothing describes how the code works, because the code and its tests already do.

## [0.1.0] - 2026-08-13

First tagged release of the AI-engineering template — the agent-driven workflow scaffold that a project copies to give its coding agents a single, current source of truth.

### Added

- **Agent instruction source of truth** — `AGENTS.md` (surfaced to Claude via `CLAUDE.md`) carrying the portable principles: deliberate model selection and task-complexity tagging, the documentation taxonomy, testing guidelines (test the real thing; verify the runtime surface), the Claude Design workflow, and the standard development workflow.
- **Documentation taxonomy under `docs/`** — Architecture Decision Records (`docs/architecture/decisions/`) with a README, numbered template, and the seed ADR-0001; how-it-works explainers (`docs/architecture/`) with an explainer template; how-to guides (`docs/guides/`); feature docs (`docs/features/`); and a security note (`docs/SECURITY.md`).
- **Feature-specification layer (`docs/specs/`)** — the design=surface / spec=behaviour boundary, with code citing the spec (never a design file) via a relative markdown anchor link, cross-cutting behaviour consolidated into one shared spec every instance cites, and no design section-anchor in user-facing copy. (Closes #1.)
- **Claude Design workflow** — brief → canvas → build-to-it → verify-and-promote, bound to a repo design system recorded in `docs/designs/DESIGN-SYSTEM.md`, with brief scaffolding under `docs/designs/briefs/`, plus the rule to validate a design against the codebase and raise the hand — by comment or brief, sized to the discrepancy — rather than silently implementing a wrong design or diverging from it in code.
- **Skills** — `epic` (turn a design doc into a phased GitHub epic, shipped one ticket at a time) and `template-feedback` (raise a reusable, project-agnostic improvement back to this upstream template).
- **MIT license** and project README.

[Unreleased]: https://github.com/dsaenztagarro/agentic-engineering-template/compare/v0.3.0...HEAD
[0.3.0]: https://github.com/dsaenztagarro/agentic-engineering-template/compare/v0.2.0...v0.3.0
[0.2.0]: https://github.com/dsaenztagarro/agentic-engineering-template/compare/v0.1.0...v0.2.0
[0.1.0]: https://github.com/dsaenztagarro/agentic-engineering-template/releases/tag/v0.1.0
