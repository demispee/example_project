---
domain: site
version: 1.0.0
status: accepted
date: 2026-10-09
---

# 000 — Site

What every page shares: how pages are built, how you move between them, how they look and
where they are published.

---

### Requirement 1: Self-contained pages [MUST]

Every page MUST be a single HTML file with its CSS and JavaScript inline. Pages MUST NOT
load scripts, styles or images from other files or from the internet. The only exception
is the optional `fonts/` folder (see Requirement 4). See ADR-0001.

**Implementation:** `index.html`, `sudoku.html`, `spot-the-difference.html`, `balls.html`

#### Scenario: A page is sent on its own

- GIVEN a single game file, for example `sudoku.html`, copied to another computer
- WHEN it is opened in a browser without an internet connection
- THEN the game works fully, only with a fallback font

**Check:** search the files for `<script src`, `<link rel="stylesheet"` and `http` URLs in
`src`/`href`; there should be none apart from links between the pages.

---

### Requirement 2: Start page [MUST]

`index.html` MUST link to every game, with its name and a one-line description.

**Implementation:** `index.html`

#### Scenario: Choosing a game

- GIVEN the start page
- WHEN the player clicks a game card
- THEN that game opens

**Check:** every game file has a card on the start page.

---

### Requirement 3: Back to the start page [MUST]

Every game page MUST show a `← back` link to `index.html`, visible at all times.

**Implementation:** `.back` link in `sudoku.html`, `spot-the-difference.html`, `balls.html`

#### Scenario: Going back

- GIVEN any game page
- WHEN the player clicks `← back`
- THEN the start page opens

#### Scenario: Bouncing balls with the panel collapsed

- GIVEN the bouncing balls page with the panel collapsed (key `H`)
- THEN the `← back` link is still visible

**Check:** open each game and click back.

---

### Requirement 4: Lab271 design system [MUST]

All pages MUST use the Lab271 dark theme: the same color tokens (`--c-canvas`,
`--c-tq`, `--c-orange`, `--c-magenta`, …), TT Interphases with its fallbacks, pill
buttons, rounded labels with a square bottom-left corner, and the `\` separator. Pages
with a scrolling layout MUST show the refracted slash top right and the Lab271 \
Schuberg Philis footer. See ADR-0002.

TT Interphases MUST load from a local `fonts/` folder when present and otherwise fall
back to Avenir Next, Poppins, Inter or the system sans serif. The font files MUST NOT be
committed.

**Implementation:** the `<style>` block of each page

#### Scenario: Fonts not available

- GIVEN a computer without the `fonts/` folder
- WHEN any page is opened
- THEN it uses the fallback fonts and the layout still fits (for example the sudoku
  heading stays on one line on a wide screen)

**Check:** compare the pages side by side; `git ls-files` lists no font files.

---

### Requirement 5: Published on GitHub Pages [SHOULD]

The site SHOULD be published with GitHub Pages from the `main` branch, so that every push
to `main` is live within minutes at https://demispee.github.io/sudoku-and-more/.

**Implementation:** repository settings on GitHub

#### Scenario: A change goes live

- GIVEN a change pushed to `main`
- WHEN the Pages build has finished
- THEN the online page shows the change

**Check:** `gh api repos/demispee/sudoku-and-more/pages/builds/latest` shows `built` for
the latest commit.
