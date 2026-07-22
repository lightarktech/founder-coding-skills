---
name: model-tiering
description: Assign the right model tier to each job — expensive brains plan and judge, cheap hands search and grind. Use when dispatching any sub-agent, configuring a multi-agent workflow, or when quota pressure appears.
---

Brain work and muscle work are different jobs. Paying brain prices for muscle work is how a week's quota disappears in days.

## The split

- **Brain (top model):** planning, final synthesis, hard-bug diagnosis, merge-conflict resolution, the deciding vote in a review.
- **Muscle (cheapest model that survives the task):** search, fetching and summarizing, per-item verification, formatting, translation, running tests.
- **Middle tier:** routine implementation against a clear spec — a mid model with tests and review beats a top model without them.

## Rules

- **Sub-agents inherit the parent's model unless told otherwise.** The parent is usually your most expensive session — *always set the model explicitly* on every dispatch. Forgetting this once cost us a 20-agent research fleet all running on the flagship.
- **Scouting is muscle work.** Reading files or web pages to summarize them never needs the top model. The expensive session reads conclusions, not raw material.
- **Escalate the hard case, not the batch.** If one item in a cheap batch turns out to be genuinely hard, send that one item up a tier. Don't promote the whole pipeline.
- **Quota pressure shrinks batches, not thinking.** Under a tight budget, cut fan-out and skip nice-to-have verification passes — never dumb down the planning or the final judgment.

## Success criteria

Every dispatch names its model on purpose. The bill's biggest line is thinking, not grinding. No flagship tokens were spent reading raw files.
