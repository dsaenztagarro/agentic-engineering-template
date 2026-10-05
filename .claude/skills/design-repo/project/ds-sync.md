# ds-sync.md — is our copy of the design system current?

`_ds/<project-id>/` is a **copy** of the shared design system, frozen when it was copied. The authoritative tree is the **`<shared>-ds` project**, readable at `/projects/<shared-project-id>/`. Nothing refreshes the copy but this project.

## The two-read check — run it before claiming anything about the design system

1. Read `/projects/<shared-project-id>/landed.md` — the design system's receipt: one grep sentinel per request that has landed.
2. Read `_ds/<project-id>/landed.md`. If it is missing, **the copy is stale**. Same verdict if its `DS-STAMP` line or its component-import count is behind the project's.

A stale copy is refreshed first. It is never a reason to re-send a request, and never a copy to compare a page against.

## When a request lands

1. The request lands in the `<shared>-ds` project.
2. That project adds a grep sentinel for it to its `landed.md`.
3. **This project re-copies `_ds/`** and re-runs the sentinel greps against it.
4. This project deletes the stand-in the landing retires, and updates the state below.

## Current state

**Verdict, <date>: the copy is CURRENT** — `DS-STAMP <stamp>`, <n> component imports, the same as the `<shared>-ds` project.

**In flight, waiting on `<shared>-ds`:** nothing. <!-- or: each component by name, and the stand-in it will retire -->

## Open questions for the design system

<!-- One line each; delete the section when there are none. -->

<!-- This file holds the current position only. What landed when goes on the tracker, not here. -->
