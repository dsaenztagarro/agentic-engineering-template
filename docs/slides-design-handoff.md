# The design handoff — Visual Reference

ASCII diagrams for the procedure in [`guide-design-handoff.md`](guide-design-handoff.md).

---

## Slide 1: Three names

```
  +-----------------------+        +-----------------------+
  |  <project>-ds         | <----> |  <project>-ds         |
  |  (repository)         |  push  |  (Claude Design       |
  |                       |  and   |   project)            |
  |  briefs, pages,       | export |                       |
  |  export mirror        |        |  pages, components    |
  +-----------+-----------+        +-----------------------+
              |
              | one generated artefact
              v
  +-----------------------+
  |  <project>            |
  |  (repository)         |
  |  code, tests, records |
  +-----------------------+
```

---

## Slide 2: Three routes into the design project

```
  a brief ........ pasted by a person ....... one ask ........... spent at ship
  /design-sync ... started by a person ...... named files ....... until overwritten
  the export ..... downloaded by a person ... the whole project .. mirrored by sync
```

A standing rule goes in the project's `readme.md`, never in a brief.

---

## Slide 3: Where a fact lives after a brief is deleted

```
  the brief carried...            lives afterwards in...
  --------------------            ----------------------
  a ruling to depict      ---->   the theme's decision record, here
  what a surface looks    ---->   the page, in <project>-ds
  what a surface does     ---->   a test, here
  work still open         ---->   an issue
  drawing instructions    ---->   nothing; git keeps the text
```
