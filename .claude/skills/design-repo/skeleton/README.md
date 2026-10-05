# __NAME__

<!-- FILL: one paragraph — what this repository designs (one application's surfaces, or what a family of applications shares), which applications consume what it generates, and the Claude Design project it mirrors. -->

This repository is the source of truth for that design.
Applications hold no copy of the export: each vendors the generated file in `dist/` and has no opinion about how it was made.

```
<!-- FILL: keep the lines that apply, delete the rest; the layout check refuses a folder not listed in the layout. -->
briefs/proposed/       the requests to the __NAME__ Claude Design project, handed over by copy-paste
pages/                 the Project export, mirrored by bin/sync — its _ds/ snapshot included
system/                the Design System export, mirrored by bin/sync; authored paths pushed up with /design-sync
references/            hand-authored material the project draws on; never touched by bin/sync
vendor/<shared>-ds/    the shared system's build inputs, copied whole by bin/vendor-sync
docs/                  the contract dist/ keeps
lib/                   the generator
dist/                  what crosses into applications — generated, committed
bin/sync               mirror a fresh export
```

## Working on it

```bash
bin/sync        # mirror ~/Downloads/__NAME__.zip; refuses an export of the wrong kind, an off-format page, or an edited upstream file
rake            # every check, then the tests — the gate before each merge
```

A hand edit inside the export folder is reverted by the next `bin/sync`: a change to what the project draws starts as a brief in `briefs/proposed/`.
