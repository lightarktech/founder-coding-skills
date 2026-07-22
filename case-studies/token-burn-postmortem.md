# How We Burned a Week's Quota in Three Days — a Postmortem with Real Numbers

> Every number below is measured from our own session logs (July 2026, building a consumer AI product on Claude Code, Max plan). Nothing is estimated for drama. This bill is why the six skills in this repo exist.

## The bill (3 days)

| Metric | Amount |
|---|---|
| Output tokens | ~20 million |
| Cache **writes** | ~370 million tokens |
| Cache **reads** | ~5 **billion** tokens |
| Result | 100% of a weekly Max-plan quota, gone by day 3 |

The surprise: output tokens weren't the killer. **Cached-context churn was.** Every long-running agent re-reads its entire accumulated history every single turn.

## The single worst offender

One repair fleet — 30 coding agents plus 10 review workflows, all on a premium model:

- **16,932 agent turns** in one campaign
- Longest single agent: **299 turns**, its context grown past 100k tokens
- That one agent re-read **~112k tokens of context per turn** near the end
- Fleet subtotal: 6.6M output tokens, **1.9 billion** cache reads

The agent wasn't just expensive. It was *getting dumber* — by turn 250 it was reasoning over a haystack of its own history (context rot). We paid premium prices for degrading judgment.

## Six bleed points (ranked)

1. **Marathon agents.** One agent chewing 7–8 tasks across 300 turns, dragging its whole history into every turn. Fix: hard contract — ≤100 turns, ≤5 tasks, hit the cap → save to disk, split into a fresh agent (see `dispatch-economics`).
2. **Flagship models doing muscle work.** "Use the strong model for coding" as a blanket rule put premium tokens on test-running and boilerplate. Fix: `model-tiering`.
3. **Reviewer armies ≈ builder armies.** 30 builders escorted by 10 review workflows; findings × verifiers grows quadratically. Fix: verification force ≤ 1/3 of build force, adversarial review capped at 2 rounds.
4. **Restarts that re-ran instead of resuming.** Client crashes killed agents 7–8 times; each "recovery" re-ran from scratch. Our logs show four duplicate copies of one session's context bill. Fix: resume from artifacts, always.
5. **The expensive session digging through files itself.** Our priciest session spent 1,192 turns and 50M cache-write tokens reading raw material a cheap scout should have summarized. Fix: scouts dig, the brain reads conclusions.
6. **Launching full fleets before the direction was pinned.** One research fleet ran twice because the question wasn't sharp the first time. Fix: `grill-founder` / interview *before* dispatch — rework is a 2× bill.

## The counterfactual, measured

After installing the rules in this repo, our first comparable job — a two-axis code review of two merged PRs — ran as **3 small agents, quoted before launch, ~290k sub-agent tokens, 5 minutes**. It caught one hard violation and two compliance-grade defects that the old process (CI green, human eyeballs) had let through.

Same depth. Roughly **1/50th** of the equivalent old-style spend. And the review was *better*, because every agent worked in a fresh, small context.

## The one-line lesson

Token bills and output quality fail together, and for the same reason: **long contexts**. Cap the context, and both problems fall over.
