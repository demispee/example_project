# ADR-0003: Sudoku difficulty is rated by the techniques a person needs

**Status:** Accepted
**Date:** 2026-10-09

## Context

A common way to set sudoku difficulty is to count the given numbers. That is a poor
measure: a puzzle with few givens can still be easy, and one with many can need an
advanced technique.

## Decision

The generator removes numbers one at a time while the solution stays unique, and rates
each candidate puzzle by solving it the way a person would. The hardest technique needed
decides the level (singles → locked candidates → pairs → triples, X-Wing, XY-Wing,
Swordfish). The number of givens is only used to spread the easiest puzzles over levels
1–3, and the number of cells left empty to spread the hardest over 7–10.

The same techniques power the `step` solver, so it can explain each step to the player.

## Consequences

- The level matches how hard the puzzle feels.
- Generating takes longer, especially for some levels, so it runs in small chunks in the
  background and has a time budget of 8 seconds.
- Levels 7–10 are puzzles these techniques cannot finish; they are rated by how much is
  left, not by a named technique. Adding chain techniques later would change how those
  levels are rated.
