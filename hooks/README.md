# Enforcement, not willpower

We wrote the three-call rule (`skills/model-tiering`), then broke it the same day — "quick" hand-done chores in a fat session. Our own skills say trust mechanisms, not willpower, so the rule got hardware: a hook that counts your session's consecutive undispatched tool calls and reminds the AI, in its own context, to send the chore to a cheap agent. Dispatching an agent resets the counter.

## Install (optional, recommended)

```bash
cp hooks/inline-gate ~/.claude/hooks/ && chmod +x ~/.claude/hooks/inline-gate
```

Then add to `~/.claude/settings.json` (merge into your existing `hooks` if you have one):

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Bash|Read|Grep|Glob|Edit|Write|NotebookEdit|Agent|Workflow",
        "hooks": [
          { "type": "command", "command": "~/.claude/hooks/inline-gate", "timeout": 5 }
        ]
      }
    ]
  }
}
```

Requires `jq`. Reminder fires at the 4th consecutive call and every 4th after; the wording tells dispatched workers to ignore it, so your agent fleet is not nagged.
