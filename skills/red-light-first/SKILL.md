---
name: red-light-first
description: Write the failing test before the fix or feature — never trust a green light you didn't first see red. Use when building any feature or fixing any bug.
---

AIs have a lazy instinct: produce code that *runs*, then produce a test that *agrees with it*. A test written after the code can pass by construction — we shipped weeks on "all green" dashboards where the tests had been quietly molded to fit broken behavior. Fake green is worse than red: red tells the truth.

## The loop

1. **Write the test first**, asserting the behavior the user actually asked for — through the public interface, not internal details.
2. **Run it. Watch it fail.** The red light proves the test can catch the problem. No red, no proof — a test you never saw fail is a decoration.
3. **Write the minimum code** that turns it green. No speculative extras.
4. **Re-run everything.** Your change must not flip other lights.

## Hard rules

- Never weaken, skip, or rewrite a failing test to make it pass. A failing test is information about the code, not an obstacle. If the test itself is genuinely wrong, say so out loud and justify it against the spec before touching it.
- One test → one implementation → repeat. Don't write twenty tests up front against imagined behavior.
- **Hostile input is a first-class test case.** Garbage dates, wrong types, negatives, empty files — a founder's users will type them, so your tests type them first. (Our own A/B run shipped a bug where an invalid date silently swallowed an expense — the missing test was exactly this one.)
- Expected values come from an independent source (the spec, a worked example) — never computed the same way the code computes them.

## Success criteria

Every new behavior has a test that was seen red before it went green. Zero tests were modified to accommodate broken code.
