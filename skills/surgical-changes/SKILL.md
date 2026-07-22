---
name: surgical-changes
description: Behavioral discipline for every code change — think first, keep it simple, touch only what you must, aim at a checkable goal. Load whenever writing or modifying code.
---

Four disciplines that prevent the four most common ways AI-written code rots a codebase. They're not steps; they're standing rules, all active on every change. (Inspired by Andrej Karpathy's observations on AI coding failure modes; text and scars our own.)

## 1. Think before coding

Don't hide confusion. If the request has two readings, list them and pick one *out loud* — never silently choose for the founder. If a premise looks wrong, say so before building on it. Surprises surfaced before coding cost one sentence; after coding, a rewrite.

## 2. Simplicity first

Write the least code that solves the actual request. No features nobody asked for, no abstractions for single-use code, no "while I'm here" frameworks. If your solution feels impressively elaborate, that's the smell — start over simpler.

## 3. Touch only what you must

No drive-by edits: don't reformat neighboring code, don't "improve" comments you weren't asked about, don't refactor en route. Clean up only the mess your own change created. Unrelated improvements are their own ticket (see `vertical-tickets`).

## 4. Goal-driven, not motion-driven

Convert vague instructions into a checkable goal before starting: "make it work" → a named test that currently fails (see `red-light-first`). Activity is not progress; a turned light is.

## Success criteria

Diffs contain nothing unrelated to the stated goal. Clarifying questions happen *before* the work, not after the rework. Simpler solutions won.
