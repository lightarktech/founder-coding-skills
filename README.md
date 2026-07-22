# founder-skills

**Claude Code skills for non-technical founders, solopreneurs, and one-person companies running an AI engineering team — no coding experience required.**

## Who this is for

- A **non-technical founder** whose AI *is* the engineering department
- A **solo founder / solopreneur** building a real product with **no software background**
- A **one-person company** using Claude Code (or any coding agent) without knowing how to read a diff
- An **indie hacker** who can describe what they want but not implement it
- Anyone whose AI plays **CTO / engineering lead** while they play CEO

If you're a working engineer, the excellent engineer-oriented packs already serve you. This pack covers the seat they leave empty.

Every popular AI-coding workflow — and they're excellent — assumes the human is an engineer who reviews diffs, approves architecture, and steers every technical fork. But a growing number of founders shipping real products with Claude Code **can't read a diff and shouldn't have to**. Their AI isn't an assistant; it's the entire engineering department. Nobody had written the operating manual for that arrangement.

This is that manual, as six installable skills. It was extracted from a real company: a non-technical, voice-typing founder and an AI engineering lead shipping a consumer app — including the week we burned our entire quota in three days and rebuilt our rules from the [autopsy](case-studies/token-burn-postmortem.md), with real numbers.

## The six skills

| Skill | One line |
|---|---|
| [`grill-founder`](skills/grill-founder/SKILL.md) | Interview the founder before coding — one question at a time, recommended answer attached, blind spots first. |
| [`decision-wiring`](skills/decision-wiring/SKILL.md) | The AI holds the architect seat; the founder sits exactly three: intent, money/values/external, acceptance. |
| [`dispatch-economics`](skills/dispatch-economics/SKILL.md) | Quote before launching agents; hard per-agent contracts (≤100 turns, ≤5 tasks); verification ≤ 1/3 of build. |
| [`loop-contract`](skills/loop-contract/SKILL.md) | No AI runs unattended without an observable exit condition. "Until it's done" is banned. |
| [`handoff-contract`](skills/handoff-contract/SKILL.md) | Moving work between sessions/tools? The receiver knows nothing — write the handoff that survives that. |
| [`model-tiering`](skills/model-tiering/SKILL.md) | Expensive brains plan and judge; cheap hands search and grind. Set the model on every dispatch, on purpose. |

They compose: `grill-founder` sharpens intent → `decision-wiring` routes the decisions → `dispatch-economics` + `model-tiering` govern the workforce → `loop-contract` boxes unattended runs → `handoff-contract` moves work without losing it.

## Install

```bash
git clone https://github.com/LightArkTech/founder-skills
cp -R founder-skills/skills/* ~/.claude/skills/
```

Restart Claude Code (or start a new session). The skills load automatically when their situations arise; you can also invoke any of them by name.

## What this is not

- Not a coding tutorial — your AI already knows how to code.
- Not a rigid pipeline — each skill stands alone; adopt one or all six.
- Not a replacement for engineer-oriented packs ([mattpocock/skills](https://github.com/mattpocock/skills), whose skill-writing philosophy — prune ruthlessly, high-signal vocabulary, explicit success criteria — this repo follows and gladly credits). If you *can* read a diff, use those too. This pack covers the seat they leave empty: the founder's.

## Receipts over vibes

The discipline here isn't theory. It came from a measured failure — ~5 billion cached tokens churned in three days — and a measured recovery: our first review job under these rules ran at ~1/50th the comparable spend and caught defects the old process missed. Details, real numbers, no drama: [case-studies/token-burn-postmortem.md](case-studies/token-burn-postmortem.md).

---

## 中文说明 (for Chinese-speaking founders)

**这是第一套专门为"非技术创始人 / 一人公司 / 独立创业者 + AI 工程队"设计的 Claude Code 技能包——完全不懂代码也能用。**

市面上所有主流 AI 编码工作流都默认"人是工程师":人来审代码、人来拍板架构。但越来越多创始人根本不懂代码,AI 就是他们的整个工程部——却没有人为这种搭档关系写过操作手册。这套就是。

六件套:`grill-founder`(动工前拷问需求:一次一题、附推荐答案、盲点优先)/ `decision-wiring`(AI 坐架构师席,创始人只坐三把椅子:产品意图、钱与价值观与对外、验收)/ `dispatch-economics`(派 AI 干活先报价;单兵合同:≤100 轮、≤5 件任务;验证兵力≤施工 1/3)/ `loop-contract`(AI 自跑必先立"出口条件",禁"干到好为止")/ `handoff-contract`(换会话/换工具不丢活的交接契约)/ `model-tiering`(贵模型只管思考与裁决,便宜模型跑腿)。

全部规则来自一家真实公司的真实事故:三天烧光一周额度、50 亿缓存 token 的账单尸检(见 case-studies,全部真实数字)。带疤的方法论,比漂亮的理论可信。

安装:克隆本仓库,把 `skills/` 下六个目录拷进 `~/.claude/skills/`,重启 Claude Code 即生效。

---

MIT © [Light Ark Technologies](https://github.com/LightArkTech) · Skill-writing philosophy credit: [Matt Pocock](https://github.com/mattpocock/skills)
