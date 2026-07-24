---
name: context-hygiene
description: Keep AI sessions short, rules in files, and context fresh. Use when sessions grow long, quality drifts, rules seem forgotten, or the founder asks why the AI "got dumber".
---

The most invisible failure mode for a non-technical founder: nothing crashed, but the AI slowly got worse. The cause is almost always context — a session dragging weeks of history, or rules that lived only in a chat that ended.

## Rules

- **Rules live in files, never in chat.** Anything meant to survive tomorrow ("from now on, always X") goes into a rules file (`CLAUDE.md`, a skill, a memory file) the moment it's decided. A rule that lives only in conversation dies with the conversation.
- **One ticket, one fresh session** for building work (see `vertical-tickets`). Long-lived "everything" chats accumulate noise the AI re-reads on every turn — you pay more *and* get dumber answers (context rot). Our own logs: agents past ~250 turns were re-reading 100k+ tokens of history per turn, at premium prices, with visibly degrading judgment.
- **The founder's own thread is exempt.** A founder's long strategy conversation is continuity, not waste — never nag them to close it. The cost lives on the AI's side: dispatch chores out, and suggest a single mid-thread compaction at a natural milestone if the session grows heavy — once, then drop it. Fresh-session discipline governs build work, not the founder's memory of their company.
- **Long chat you can't leave? Compact it.** Summarize-and-continue (e.g. `/compact`) rebuilds the context and reloads the current rules. Even better when picking up old work: close and *resume* the session — full history kept, rules loaded fresh.
- **New rules don't reach old sessions.** Sessions load rules at start. After changing the rules files, restart or compact any session that must follow them — don't assume it noticed.
- **End of session = write the state down.** Before closing mid-project, save status to a file or write a handoff (see `handoff-contract`). "The AI will remember" is false; files remember.

## Success criteria

No working session needed the phrase "as I told you before". Rule changes reached every active session the same day. Nothing important exists only inside a closed chat.
