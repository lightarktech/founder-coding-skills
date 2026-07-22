---
name: dispatch-economics
description: Cost and quality discipline for dispatching sub-agents, background workers, or multi-agent workflows. Use before launching any agent fleet or long-running autonomous task, and whenever someone mentions burning through quota or budget.
---

Quality first, tokens second — and they align. A single agent grinding for hundreds of turns doesn't just cost more; it gets *worse* (context rot: by turn 200 it re-reads a bloated history every turn and reasons over noise). Small, fresh-context units are both cheaper and smarter.

We learned this on a real bill: three days, one week's entire quota, ~5 billion cached-context tokens read. The autopsy is in [case-studies/token-burn-postmortem.md](../../case-studies/token-burn-postmortem.md).

## Rules

- **One agent per ticket by default.** A fleet needs all three preconditions:
  1. **Quote first** — say out loud, before launch: how many agents, how long, estimated tokens.
  2. **Per-agent contract** — ≤100 turns, ≤5 tasks; hit a cap → save progress to disk, report, split into a fresh agent.
  3. **True parallelism only** — fan out only work items with no dependencies on each other.
- **Verification force ≤ 1/3 of build force.** Reviewer armies grow quadratically if you let them (N findings × M verifiers). Cap adversarial review at 2 rounds — converged means stop; there is no "one more round for safety".
- **Slice work vertically.** A ticket = one thin end-to-end feature (schema + logic + UI + test) that fits in a single fresh context window. Never slice by technical layer — layer-slices create the 300-turn monster agents.
- **The expensive session never digs.** Your main (priciest) session dispatches a cheap scout to read files or the web and consumes its conclusion. Thinking at the top, grinding at the bottom.
- **Restarts resume, never re-run.** Crashed work restarts from its saved artifacts. Re-running from scratch doubles the bill for zero new value.

## Success criteria

Every dispatch was quoted before launch. No agent exceeded its contract. The bill correlates with shipped output — and the top line item is thinking, not grinding.
