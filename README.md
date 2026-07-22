# founder-coding-skills

**The one skill pack for founders who never wrote code — running a software company on Claude Code with an AI engineering team. Install this, and you're set: nothing else to assemble.**

## Who this is for

- A founder who is **not a programmer by background** — and isn't going to become one
- A **solo founder / solopreneur** building a real product with **no software experience**
- A **one-person company** where the AI *is* the entire engineering department
- An **indie hacker** who can describe what they want but not implement it
- Anyone whose AI plays **CTO / engineering lead** while they play CEO

Every popular AI-coding workflow assumes the human is an engineer who reviews diffs and approves architecture. If that's you, great — you have options. If it's *not* you, until now you had to duct-tape rules together from packs written for engineers. This pack is the complete operating manual for the other arrangement: **you run the company, the AI runs the engineering — thirteen skills, two layers, one install.**

Extracted from a real company: a non-programmer, voice-typing founder and an AI engineering lead shipping a consumer app — including the week we burned our entire quota in three days and rebuilt our rules from the [autopsy](case-studies/token-burn-postmortem.md), with real numbers.

## Built for Claude Code's frontier models — on purpose

This pack is designed for **Claude Code running Anthropic's strongest models** (Opus-class and above — the tier a **Max subscription** buys), and we say so openly. Three reasons:

1. **A non-programmer founder has no safety net.** An engineer using AI can catch its mistakes in the code; you can't. Your model isn't *assisting* your engineering — it **is** your engineering. When the CTO seat is filled by a model, you hire the strongest one that exists, not a cheaper intern you can't supervise.
2. **The skills are written in frontier style.** Every skill here is a lean behavioral contract — goals, boundaries, success criteria — with the step-by-step hand-holding deliberately left out. That follows Anthropic's own authoring guidance ("assume Claude is already very smart"), and published benchmarks showing over-explaining actively *hurts* top models. A weaker model needs the scaffolding we removed; a frontier model is freed by its absence.
3. **The economics were measured here.** `dispatch-economics` and `model-tiering` are calibrated on real Claude Code Max-plan quota mechanics — our postmortem *is* a Max-plan bill. Sub-agent dispatch, per-dispatch model selection, background agents: the pack assumes Claude Code's premium feature line, because that's what a one-person software company actually runs on.

Honest scope: designed and battle-tested **only** on Claude Code with frontier Claude models. On weaker models or other coding agents, unverified — and the writing style is intentionally not for them.

## One install

```bash
git clone https://github.com/lightarktech/founder-coding-skills && cp -R founder-coding-skills/skills/* ~/.claude/skills/
```

One line, then restart Claude Code (or start a new session). All thirteen skills load automatically when their situations arise — you never have to invoke them by hand, though you can.

## Layer 1 — How you run the team (founder-facing)

| Skill | One line |
|---|---|
| [`grill-founder`](skills/grill-founder/SKILL.md) | The AI interviews *you* before coding — one question at a time, recommended answer attached, blind spots first. |
| [`decision-wiring`](skills/decision-wiring/SKILL.md) | The AI holds the architect seat; you sit exactly three: intent, money/values/external, acceptance. |
| [`dispatch-economics`](skills/dispatch-economics/SKILL.md) | The AI quotes before launching agent fleets; hard per-agent contracts (≤100 turns, ≤5 tasks). |
| [`loop-contract`](skills/loop-contract/SKILL.md) | No AI runs unattended without an observable exit condition. "Until it's done" is banned. |
| [`handoff-contract`](skills/handoff-contract/SKILL.md) | Moving work between sessions or tools without silently losing it. |
| [`model-tiering`](skills/model-tiering/SKILL.md) | Expensive brains plan and judge; cheap hands search and grind. |
| [`bad-news-first`](skills/bad-news-first/SKILL.md) | Your AI reports the truth — failures first, proof attached, no cheerleading. |
| [`context-hygiene`](skills/context-hygiene/SKILL.md) | Why AIs "get dumber" in long chats, and the session habits that prevent it. |

## Layer 2 — How your AI does the work (engineering discipline)

You never touch these — they discipline the AI itself. They're why you can *not* read the code and still trust it.

| Skill | One line |
|---|---|
| [`vertical-tickets`](skills/vertical-tickets/SKILL.md) | Work slices into thin end-to-end features you can see working — never into invisible technical layers. |
| [`red-light-first`](skills/red-light-first/SKILL.md) | Every feature's test must fail first, then pass — kills the fake-green tests AIs love to write. |
| [`bug-autopsy`](skills/bug-autopsy/SKILL.md) | No guess-and-patch: reproduce, shrink, prove the cause, then fix exactly that. |
| [`surgical-changes`](skills/surgical-changes/SKILL.md) | Think first, keep it simple, touch only what you must, aim at a checkable goal. |
| [`two-axis-review`](skills/two-axis-review/SKILL.md) | Finished work gets judged twice — built right? built the *right thing*? — and one pass never excuses the other. |

They compose: `grill-founder` sharpens what you want → `vertical-tickets` slices it → `dispatch-economics` + `model-tiering` staff it → `red-light-first` + `surgical-changes` build it → `two-axis-review` checks it → `bad-news-first` tells you the truth about it → `loop-contract` + `handoff-contract` + `context-hygiene` keep the whole thing from quietly rotting.

## Receipts over vibes

The discipline here isn't theory. It came from a measured failure — ~5 billion cached tokens churned in three days — and a measured recovery: our first review job under these rules ran at ~1/50th the comparable spend and caught defects (including a one-word legal-wording deviation) that the old process missed. Real numbers, no drama: [case-studies/token-burn-postmortem.md](case-studies/token-burn-postmortem.md).

## Credits

Skill-writing philosophy (prune ruthlessly, high-signal vocabulary, explicit success criteria): [Matt Pocock](https://github.com/mattpocock/skills). Behavioral-discipline inspiration: Andrej Karpathy's public observations on AI coding failure modes. Code-smell canon: Martin Fowler's *Refactoring*. All skill text here is original, and every rule was paid for with our own incidents. If you *are* a working engineer, Pocock's pack is excellent alongside this one — Layer 2 gives you the essentials without leaving the founder's seat.

---

## 中文说明 (for Chinese-speaking founders)

**这是唯一一套"装完就齐"的 Claude Code 技能包,专为非程序员出身的创始人 / 一人公司 / 独立创业者设计——完全不懂代码,也能开软件公司、写出世界级的软件。装这一个,其他都不用装。**

**为什么明确只针对 Claude Code 旗舰模型线(Max 订阅)**:①非程序员创始人没有安全网——工程师能亲自看代码兜底,你不能;模型不是"辅助"你的工程部,它**就是**你的工程部,CTO 的位子必须请全世界最强的模型来坐;②本包所有 skill 都按"前沿模型写法"写成(只给目标、边界、完成判据,刻意不给保姆式步骤——官方指引与公开基准都证明:对顶级模型,啰嗦反而有害),弱模型需要的搀扶我们刻意没放;③包里的经济学规则(报价/单兵合同/模型分层)全部在真实的 Claude Code Max 订阅账单上校准过。诚实声明:仅在 Claude Code + 旗舰 Claude 模型上实测,其他环境未验证。

十三件 skill,两层:

**第一层·你怎么管 AI 工程队(8 件)**:`grill-founder`(动工前 AI 反过来拷问你:一次一题、附推荐答案、专挖你的盲点)/ `decision-wiring`(AI 坐架构师席,你只坐三把椅子:产品意图、钱与价值观与对外、验收)/ `dispatch-economics`(AI 派兵先向你报价;单兵合同 ≤100 轮 ≤5 件事)/ `loop-contract`(AI 自跑必先立"出口条件")/ `handoff-contract`(换会话换工具不丢活)/ `model-tiering`(贵模型思考,便宜模型跑腿)/ `bad-news-first`(坏消息先说、"完成"必带证据、禁报喜不报忧)/ `context-hygiene`(AI 越聊越笨的真相与会话卫生习惯)。

**第二层·你的 AI 怎么干活(5 件,你不用碰,它自动遵守)**:`vertical-tickets`(活按"你能看见的功能"切,不按你看不见的技术层切)/ `red-light-first`(测试先见红灯再变绿,封杀 AI 爱写的假绿测试)/ `bug-autopsy`(修 bug 禁瞎猜,先复现、再定罪、只修真凶)/ `surgical-changes`(想清楚再动手、能简单不复杂、只碰该碰的)/ `two-axis-review`(完工双轴审:做得对不对 × 做的是不是你要的)。

全部规则来自一家真实公司的真实事故:三天烧光一周额度、50 亿缓存 token 的账单尸检(见 case-studies,全部真实数字)。带疤的方法论,比漂亮的理论可信。

**安装(一行)**:`git clone https://github.com/lightarktech/founder-coding-skills && cp -R founder-coding-skills/skills/* ~/.claude/skills/` 然后重启 Claude Code 即全部生效。

---

MIT © [Light Ark Technologies](https://github.com/lightarktech)
