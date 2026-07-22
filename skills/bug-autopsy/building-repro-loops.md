# Building the Red Light — a Catalog

The whole skill is Phase 1: getting one command that reliably shows the bug. Everything after is mechanical. Ways to build that command, roughly in order of preference:

1. **A failing test** at whatever public boundary reaches the bug.
2. **A curl / HTTP script** against a running dev server, asserting on the response.
3. **A CLI invocation** with a fixture input, diffed against known-good output.
4. **A headless browser script** driving the UI, asserting on the page or console.
5. **A captured-trace replay** — save the real request/payload/event that misbehaved, replay it through the code path in isolation.
6. **A throwaway harness** — boot the minimal slice of the system (one service, stubbed dependencies) that exercises the bug in a single call.
7. **A brute loop** — for "sometimes wrong" bugs, run hundreds of random inputs and count failures.
8. **A bisect harness** — if the bug appeared between two known-good states, script "boot at state X, check" so version-bisection can run unattended.
9. **A differential run** — same input through old vs new version (or two configs), diff the outputs.

## Tighten it

A loop is a product; improve it before using it:

- **Faster** — cache setup, skip unrelated boot steps, narrow the scope. A 2-second loop is a superpower; a 30-second flaky one is barely better than none.
- **Sharper** — assert the user's exact symptom, not "didn't crash".
- **Deterministic** — pin the clock, seed the randomness, isolate the filesystem, freeze the network.

## Non-deterministic bugs

Don't chase a perfect repro; raise the reproduction *rate* until it's debuggable. Loop the trigger 100×, add parallelism and stress, shrink timing windows with injected sleeps. A bug at 50% is workable; at 1% it isn't — keep raising the rate.

## When you truly can't build one

Say so explicitly, list what you tried, and ask for one of: access to the environment that reproduces it, a captured artifact (log dump, network trace, recording with timestamps), or permission to add temporary instrumentation. **Do not proceed to theories without a loop** — reading code to build a story first is exactly the failure this discipline exists to prevent.

## Instrumentation manners

- Prefer one breakpoint or REPL probe over ten log lines; never "log everything and grep".
- Tag every temporary log with one unique prefix (e.g. `[DBG-3f]`) so cleanup is a single search. Untagged debug logs are the ones that ship.
- For performance bugs, logs lie — measure first (timer, profiler, query plan), bisect second.
