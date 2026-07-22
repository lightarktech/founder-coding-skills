---
name: loop-contract
description: Write an exit-condition contract before letting any AI run unattended — a background agent, a scheduled loop, a "keep going until it works" task. Use whenever work is handed off to run without a human watching.
---

Never launch "until it's done". "Done" is not observable; loops without observable exits run forever, burn budget, and drift. Fill this contract first — every field, before launch:

```
GOAL      One sentence: take X from state A to state B.
DONE      Observable end state ("tests green + lint clean + PR open").
          Banned: "done", "polished", "production ready", "good enough".
SCALE     ≤100 turns, ≤5 tasks. Hitting a cap = save progress, report, split.
STOP      Reached DONE / hit a cap / stuck needing a human → stop and report.
RETRY     Not DONE and moves remain → read the last failure, change ONE
          variable, retry. Never shotgun multiple changes per iteration.
VERIFY    How it checks its own work: tests, an independent evaluator,
          or adversarial review (max 2 rounds).
FIRST     Context + what to check before starting — a fresh session
          knows nothing about this conversation.
RED LINES What it must never touch (production, user data, permissions,
          anything irreversible).
```

Trust mechanisms, not luck: the point is to put unattended work inside a box that is observable, correctable, and reversible.

## Success criteria

A stranger could run the loop from the contract alone. The loop cannot run forever — every path leads to DONE, a cap, or a report.
