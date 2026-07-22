---
name: bug-autopsy
description: Structured diagnosis for bugs — no guess-and-patch. Use when something is broken, throwing, failing, or slow and the cause isn't already proven.
---

The expensive failure mode isn't the bug — it's an AI *guessing* at the cause and "fixing" code it never proved guilty. Guess-patches breed regressions, and three guess-patches deep, nobody knows what the system even does anymore.

For the full catalog of ways to build and tighten a repro loop, see [building-repro-loops.md](building-repro-loops.md).

## The discipline

1. **Build a red light first.** Before any theory, construct one command that reliably shows the bug — a failing test, a script, a curl. If you can't trigger it on demand, you don't understand it yet; keep working on the trigger, not the theory. For flaky bugs, raise the reproduction rate until it's debuggable — loop it 100×, pin the randomness, narrow the timing.
2. **Shrink it.** Cut inputs and steps one at a time until everything that remains is load-bearing. A minimal repro shrinks the suspect list for free.
3. **List 3 candidate causes before testing any.** One-hypothesis debugging anchors on the first plausible story. Each candidate must make a testable prediction: "if X is the cause, changing Y makes it disappear."
4. **Test one variable at a time.** A probe that changes two things proves nothing.
5. **Fix the proven cause only.** No drive-by cleanups in the same change.
6. **Re-run the red light** — now green — plus the full test suite. Turn the repro into a permanent regression test.

## Hard rules

- No repro, no patch. "It's probably X" is not a diagnosis.
- Production systems get read-only inspection; every change goes through the normal review path.
- Close with a report: root cause, lines changed, proof of the fix.

## Success criteria

The commit message names the proven cause. The repro is now a regression test. Nothing unrelated changed.
