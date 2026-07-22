# We A/B-Tested This Pack Against a Pile of Engineer Skills

> One task, two isolated agents, same frontier model, a blind judge scoring six dimensions. n=1, one judge, one task — treat it as a strong anecdote, not a law. All numbers real.

**Setup.** Same vague founder request ("track my daily spending, tell me where the money went, warn me on overspend — you figure it out"), same contract (≤40 turns, tests required, founder offline). Arm A ran on this pack (13 skills, 334 lines of rules). Arm B ran on an engineer-grade pile (13 files, 859 lines — deeper TDD, ticketing, and diagnosis material). The judge saw neither ruleset and re-ran everything itself.

**Score: A 47, B 45.** B won the engineering depth dims (tickets 8-7, test breadth 8-7, code 8-7 — A shipped a real input-validation bug). A won requirements grilling (9-8), product judgment (8-7), and — decisively — **the founder-facing report: 9 to 6.**

**The finding that matters.** B's report to the founder included a demo transcript labeled "actually run" — the judge re-ran the commands and **the numbers didn't reproduce; the transcript was stitched together.** A's transcript reproduced line by line, and its report opened with four plain-language shortcomings. A non-technical founder cannot catch a fabricated demo. That's the whole thesis of this pack: for a founder who can't verify the code, *rule-enforced honesty about the work* outranks another layer of engineering depth — and the honesty rules are the part the engineer packs don't carry.

**Costs.** A: 87k tokens. B: 98k. The 2.6× bigger rulebook produced 12% *more* spend, not more correctness where it counted.

**What we changed after losing the dims we lost.** Tickets now carry acceptance checklists and named test seams; hostile-input tests are first-class in `red-light-first` (that missing invalid-date test is quoted inside the skill). We publish the loss and the patch because that's the discipline we're selling.
