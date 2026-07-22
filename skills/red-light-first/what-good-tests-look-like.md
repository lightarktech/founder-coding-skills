# What a Test Worth Keeping Looks Like

A good test reads like a promise to the user — "a saved expense survives a restart" — and survives refactors, because it checks *behavior through the public boundary*, never internal wiring. Code can be rewritten entirely; the promises shouldn't move.

## Test at agreed boundaries

A **boundary** (seam) is where you observe behavior from outside: the module's public interface, the CLI, the HTTP endpoint. Pick the boundaries *before* writing tests, and prefer the highest one that still gives a crisp signal — fewer boundaries, better tests. Testing at internals means every refactor breaks tests that were never protecting anything.

## The three test smells that rot suites

- **Implementation-coupled** — it stubs internal collaborators, pokes private functions, or verifies through a side door (querying the database directly instead of using the interface). Tell: refactoring breaks it while behavior didn't change.
- **Self-confirming** — the expected value is computed the same way the code computes it (`assert add(a,b) == a+b`), so it can never disagree. Expected values come from an independent source: a hand-worked example, the spec, a known-good literal.
- **Bulk-imagined** — twenty tests written up front against guessed behavior, then code bent to fit. Work one test → one implementation at a time; each cycle teaches the next.

## Stubbing rules (mocks)

- Stub **only at the edges you don't own** — the network, the clock, the payment provider. Never stub your own internals to "make the test easier"; that's the implementation-coupled smell wearing a costume.
- If a test needs five stubs to run, the code under test is doing too much — that's design feedback, not a testing problem.
- A stubbed dependency needs at least one真 integration test somewhere proving the real edge actually behaves as the stub claims.

## Hostile input is not optional

Wrong types, garbage dates, negatives, empty and corrupted files: real users type all of it. Our own A/B run shipped a silent-data-loss bug whose missing test was exactly "what if the date is nonsense". Budget hostile-input tests into every ticket, not as a someday.
