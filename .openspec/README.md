# OpenSpec — Sudoku and more

Specifications and design decisions for this project. The specs say **what** each page
must do; the ADRs say **why** it is built the way it is.

## Workflow

1. **Spec first.** Before changing behavior, add or update the requirement in the spec.
2. **Build.** Implement the change so it matches the spec.
3. **Check.** After every change, check that all requirements of the affected spec still
   hold. There are no automated tests yet, so each requirement lists a manual check.

If the code and the spec disagree, one of them is wrong: fix the code, or update the spec
on purpose.

## Specs

| # | Spec | Covers |
|---|------|--------|
| [000](specs/000-site/spec.md) | Site | Single-file pages, start page, back links, design system, hosting |
| [001](specs/001-sudoku/spec.md) | Sudoku | Generator, difficulty 1–10, input, notes, hints, step solver |
| [002](specs/002-spot-the-difference/spec.md) | Spot the difference | Scenes, rounds, clicks, penalties, records |
| [003](specs/003-bouncing-balls/spec.md) | Bouncing balls | Physics, colors, controls |

## ADRs

| # | Decision | Status |
|---|----------|--------|
| [0001](adr/0001-single-file-pages.md) | Every page is one self-contained HTML file | Accepted |
| [0002](adr/0002-lab271-design-system.md) | All pages use the Lab271 design system; licensed fonts stay out of the repo | Accepted |
| [0003](adr/0003-difficulty-by-human-techniques.md) | Sudoku difficulty is rated by the techniques a person needs | Accepted |

## Format

Each requirement in a spec has:

- a title with **MUST**, **SHOULD** or **MAY** (RFC 2119)
- a short description
- `**Implementation:**` the file and function that implement it
- at least one `#### Scenario:` in GIVEN / WHEN / THEN form
- `**Check:**` how to verify it by hand

ADRs are numbered `NNNN-title.md` and are never deleted. A decision that is replaced gets
the status *Superseded by NNNN*.
