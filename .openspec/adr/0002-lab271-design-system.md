# ADR-0002: All pages use the Lab271 design system

**Status:** Accepted
**Date:** 2026-10-09

## Context

The sudoku was restyled in the Lab271 design system of Schuberg Philis. The other pages
had their own look (a gold, glamorous style for spot the difference and rainbow colors for
the balls), so the site did not feel like one whole.

Lab271 uses TT Interphases, a licensed font that may not be redistributed. The Lab271 and
Schuberg Philis logos are trademarks.

## Decision

- All pages use the Lab271 dark theme: the same color tokens, type, buttons, labels,
  slash and footer.
- The spot-the-difference artwork keeps its own colors; only the interface around it and
  the markers follow the theme.
- TT Interphases loads from a local `fonts/` folder that is ignored by git. Without it,
  pages fall back to Avenir Next, Poppins, Inter or the system sans serif.
- The logos are inline SVG and are excluded from the Apache 2.0 license (see README).

## Consequences

- Visitors without the font see a fallback, which is wider. Layouts must leave room for
  that (the sudoku heading was widened from 640 to 760 px for this reason).
- The repository is open source except for the logos.
- Removing the Schuberg Philis branding later means changing every page.
