---
name: design-handoff
description: The Claude Design handoff loop — which repository is which, the three routes into the design project, writing a brief, reading an export back, and closing a brief out. Use when writing a design brief, handing work to Claude Design, reading an export back into the design repository, or building a surface from a design page.
---

# Working with Claude Design: the handoff loop

How a design change gets from an idea to something this application renders, and what an agent may and may not touch on the way.
This is an operating procedure — the order matters, and two of its steps exist to stop a class of silent loss.

If this project has no user interface, delete this skill and the design row of `AGENTS.md`.

## 1. Three names, and which one you are in

| | what it is | you may edit it |
|---|---|---|
| **`<project>`** (this repository) | the application — code, tests and decision records | yes |
| **`<project>-ds`** (the design repository) | the briefs, the pages Claude Design returns, a mirror of the design project's export, and the generator for the one artefact that crosses | the briefs and what the repository authors — yes; the export mirror, never (§3) |
| **`<project>-ds`**, the Claude Design project | where pages, components and specimens are drawn | through the three routes in §2, never directly |

<!-- FILL: the real names, and a fourth row if a shared design system is vendored into the design repository. -->

The design repository and the design project share a name. Say *repository* or *project*: the difference decides whether an edit survives.

Design content lives outside this repository because it grows without bound, and an application repository carrying it stops being code — one terminal client's pages reached 920 KB before they were moved out.

## 2. What crosses, and by which route

**Exactly one generated artefact reaches this application**, and it is data — a token set, or a stylesheet bundle.
<!-- FILL: the artefact, its path here, and the command that vendors it. -->
A page is read by a person designing or building a surface; it is never a build input, and code never cites one.

The design project holds its own files and nothing else — it cannot open either repository. Everything it knows arrives by one of three routes, each started by a person:

| route | carries | lifetime |
|---|---|---|
| **a brief**, pasted into the project | one ask | spent on arrival; deleted when its surface ships (§6) |
| **`/design-sync`**, from Claude Code | named files, under a plan the person approves | until overwritten |
| **the export**, downloaded as a zip | the whole project, back to the design repository | a commit of the mirror |

`/design-sync` needs a claude.ai login in Claude Code, and is unavailable on Bedrock, Vertex and Foundry. It writes one change at a time, never as a wholesale replace.

- **A rule that must hold for every future export goes into the project's own `readme.md` through `/design-sync`**, which the project reads before it draws. Pasted into a brief, the same rule dies with the brief.
- **The mirror is refreshed only through the export** and the design repository's sync script, whose refusals — an export that is not a design system's, a file the repository owns that the project edited — are the review gate.

## 3. The export mirror is generated — never hand-edit it

The sync script mirrors the export with `rsync -a --delete`. A hand-edit there is destroyed by the next sync, silently, and it makes the record lie: the mirror is committed so its diff shows what Design produced.
Commit the mirror as produced, defects included, with what you found named in the commit message — and fix it through a brief.

If the design repository authors a file the project draws against — a checked palette — that file flows **up** through `/design-sync`, and the sync script refuses an export that disagrees with it.

## 4. The loop

```
  a brief in <project>-ds/briefs/proposed/
        |
        v
  pasted into the design project                  <- a person
        |
        v
  the project draws it; export downloaded         <- a person
        |
        v
  in <project>-ds: sync, regenerate, run the suite
        |
        v
  review the sync diff: a rule changed or only a comment?
  every changed page well-formed? a removal that orphaned a heading?
        |
        v
  commit the mirror, as produced; a defect becomes a new brief
        |
        v
  in this repository: vendor the artefact
        |
        v
  build the surface against the page; tests hold the behaviour
        |
        v
  close out the brief it satisfied                brief-closer
```

**The last step is the one that gets skipped**, because nothing fails when it is.

## 5. Writing a brief

1. **State the constraint; do not cite the artefact.** A decision's ruling is written out as a sentence, with its theme named beside it. A link out of the design repository resolves to nothing at the far end.
2. **Every proper noun must resolve inside the design project.** Pages, components, tokens — yes. File paths, commands, frameworks, issue numbers — no.
3. **A brief never cites another brief.** Each is deleted on its own schedule.
4. **A technical decision belongs in a decision record here, not in the design.** The brief asks Design to *depict* a ruling, never to make it. A behaviour the page must show that nothing has settled is drawn and labelled as an **open question**, never as a rule.

## 6. Closing a brief out

A brief ends when its surface ships here, so the ticket that ships a surface carries a checkbox to delete its brief. Before the deletion: verify each ask in the design project's export, re-point everything that cited the brief, rewrite future-tense prose about it, and close the tracking issue.

A brief whose asks all landed closes. One where some did not stays, with the remainder reported. One that got what it asked for while the doing broke something else closes, and owes a follow-up brief. The **`brief-closer`** agent does this, and verifies before it deletes.

## 7. What an agent must not do

- **Edit the export mirror**, or the vendored artefact here.
- **Style anything outside the vendored artefact** — a colour, a spacing, a component the design system does not ship. The fix is a brief, not a local rule.
- **Cite a brief or a design page from code.** Cite the decision record for *why* and the test for *what*.
- **Answer a behaviour question on a page.** Behaviour is decided here, in a test.
- **Start a route that §2 says a person starts.**
