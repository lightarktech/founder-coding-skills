---
name: two-axis-review
description: Review finished work on two separate axes — craft quality and faithfulness to what was asked — and never let one axis excuse the other. Use before merging any meaningful change.
---

A change can be beautifully built and still be the wrong thing; it can be exactly what was asked and still be built badly. One review that mixes both questions lets each failure hide behind the other's pass. Keep the axes separate.

## Axis 1 — Craft

Does the change meet this project's own standards? Documented conventions first; beyond them, watch for the classics: duplicated logic, names that don't say what they mean, one edit scattered across a dozen files, abstractions nobody needed. (The canon here is Martin Fowler's catalog of code smells — flag by name, as judgment calls, never as autopilot rules.)

## Axis 2 — Faithfulness

Put the original request next to the diff and check three things:
- **Missing** — asked for, not there (or half there).
- **Uninvited** — there, but nobody asked (scope creep hiding as initiative).
- **Warped** — looks implemented, but numbers/edge behavior/wording differ from what was specified. Check the exact values: limits, thresholds, orderings, legal wording.

## Rules

- Run the two axes as **separate passes with fresh eyes** (two sub-agents, or two sittings) so they can't contaminate each other.
- Report per axis; don't average them into one score. "9/10 craft" never buys forgiveness for "wrong feature".
- Adversarial rounds cap at 2 (see `dispatch-economics`). Findings must quote the line they're about.
- Our first run of this review caught a legally sensitive one-word deviation ("we" vs "I" in a compliance sentence) that CI and human eyes had both passed. Exact-wording checks pay.

## Success criteria

Two written verdicts, one per axis, each citing evidence. Every finding is either fixed or explicitly accepted with a reason — none silently dropped.
