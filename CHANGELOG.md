# Changelog

All notable changes to this project are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Changed

- **Renamed to `agentic-engineering-template`.** "AI engineering" names building applications on language models; this template is about engineering *with* agents.
- **Every corpus an agent reads is bounded.** Decision records move to `docs/adr/`: one per theme, at most ten, each under sixty lines, amended in place, with superseded reasoning on a per-theme decision-log issue. `/epic` amends themes once, at close-out, instead of writing a record per ticket. `docs/adr/0001-decision-records.md` records why.
- **Design content moves to a sibling `<project>-ds` repository**, with one generated artefact crossing. `docs/guide-design-handoff.md` and its slides are the procedure, including the three routes into a Claude Design project.

### Added

- **`.github/workflows/docs.yml`**, which fails the build on an eleventh record, a record over sixty lines, or a folder that grows one file per work item.
- **A `brief-closer` agent**, which closes a brief once its surface ships and verifies each ask before deleting anything.

### Removed

- **`docs/features/`, `docs/specs/`, `docs/guides/`, `docs/architecture/` and `docs/designs/`.** Each grew one file per feature, decision or brief. Behaviour is stated by tests, the reasoning by themed records, and a mechanism worth explaining by one topic guide.

## [0.1.0] - 2026-08-13

First tagged release of the AI-engineering template — the agent-driven workflow scaffold that a project copies to give its coding agents a single, current source of truth.

### Added

- **Agent instruction source of truth** — `AGENTS.md` (surfaced to Claude via `CLAUDE.md`) carrying the portable principles: deliberate model selection and task-complexity tagging, the documentation taxonomy, testing guidelines (test the real thing; verify the runtime surface), the Claude Design workflow, and the standard development workflow.
- **Documentation taxonomy under `docs/`** — Architecture Decision Records (`docs/architecture/decisions/`) with a README, numbered template, and the seed ADR-0001; how-it-works explainers (`docs/architecture/`) with an explainer template; how-to guides (`docs/guides/`); feature docs (`docs/features/`); and a security note (`docs/SECURITY.md`).
- **Feature-specification layer (`docs/specs/`)** — the design=surface / spec=behaviour boundary, with code citing the spec (never a design file) via a relative markdown anchor link, cross-cutting behaviour consolidated into one shared spec every instance cites, and no design section-anchor in user-facing copy. (Closes #1.)
- **Claude Design workflow** — brief → canvas → build-to-it → verify-and-promote, bound to a repo design system recorded in `docs/designs/DESIGN-SYSTEM.md`, with brief scaffolding under `docs/designs/briefs/`, plus the rule to validate a design against the codebase and raise the hand — by comment or brief, sized to the discrepancy — rather than silently implementing a wrong design or diverging from it in code.
- **Skills** — `epic` (turn a design doc into a phased GitHub epic, shipped one ticket at a time) and `template-feedback` (raise a reusable, project-agnostic improvement back to this upstream template).
- **MIT license** and project README.

[0.1.0]: https://github.com/dsaenztagarro/agentic-engineering-template/releases/tag/v0.1.0
