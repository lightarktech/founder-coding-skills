---
name: handoff-contract
description: Write a self-contained handoff when work moves to a new session, a different AI tool, or another person. Use when context is about to be lost — quota exhausted, switching tools, ending a session mid-project.
---

The receiver knows **nothing**. Not your conversation, not your decisions, not your file layout. A handoff that assumes shared memory silently loses work — we watched a receiving tool merge a pull request into a dead branch because the handoff skipped one re-review rule, and the work vanished for days before anyone noticed.

## A handoff must contain

1. **Status snapshot** — what is done, and *how it was verified* (test counts, CI links). Not "mostly finished".
2. **Rules of the road** — the 5–8 constraints that actually bind (what never to touch, what needs approval, what "tests may not be weakened" means here). Not your whole culture doc.
3. **Environment recipe** — exact commands to reach a working state, copy-pasteable.
4. **Task list with per-task exit conditions** — each task states its own observable "done".
5. **Overall exit** — when the whole handoff is complete, in checkable terms.
6. **Not-yours list** — parked items and escalation paths, so the receiver doesn't "helpfully" wander into them.
7. **File map** — where the five things they'll look for actually live.

Write facts, not vibes. Every claim verifiable, every exit observable.

## Success criteria

The stranger test: someone with zero context could execute the handoff end to end. If any step requires "ask the previous session", the handoff failed.
