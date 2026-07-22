---
name: vertical-tickets
description: Slice work into thin end-to-end feature tickets, never into technical layers. Use when breaking any plan, spec, or feature request into workable units.
---

How you cut the work decides how it fails. Layer-cuts ("first the database, then the backend, then the UI") mean nothing is demoable until everything is done — and they breed marathon agents: we watched one chew through 8 layer-tasks across 299 turns, getting slower and dumber as its context bloated.

## The rule

A ticket is a **vertical slice**: one narrow feature path cut through *every* layer — data, logic, interface, test — that a user (or the founder) can see working on its own.

- **Sized to one sitting:** the whole ticket fits in a single fresh AI context window. If it doesn't fit, it's two tickets.
- **Independently verifiable:** each finished ticket is demoable — the founder can try it and say "yes, that's it" (see `decision-wiring`, seat 3).
- **Carries its own acceptance checklist:** each ticket lists the checkable items that mean "done", and names the seam its tests will hit (the public interface, agreed up front). A ticket without a checklist is a wish.
- **Declares its blockers:** each ticket names which tickets must land first. No blockers = can start now, in parallel.
- **One ticket, one agent, one fresh context.** The ticket boundary *is* the agent contract boundary (see `dispatch-economics`).

## The exception

A **wide mechanical change** (rename something used everywhere) can't slice vertically — one edit breaks a thousand call sites. Sequence it as expand → migrate in batches → contract: add the new form alongside the old, move callers over batch by batch with everything staying green, delete the old form last.

## Success criteria

Every ticket ends in something demoable. No agent ever inherits a second ticket in the same context. The founder saw progress this week, not "80% done" for three weeks.
