# The Ticket Template

Every ticket carries these fields. A ticket missing one isn't ready to dispatch.

```
TITLE        Verb + outcome ("Record one expense from the CLI")
DELIVERS     The end-to-end behavior a founder could try after this lands
BLOCKED BY   Ticket numbers that must land first (none = start now)
BOUNDARY     The public interface its tests will hit (agreed up front)
ACCEPTANCE   Checkboxes, each observable:
             [ ] happy path works end to end (name the exact command/tap)
             [ ] hostile input rejected loudly (name the inputs)
             [ ] tests seen red, then green
             [ ] demo note written for the founder (one sentence + how to try)
SIZE CHECK   Fits one fresh context window? If unsure, split before dispatch.
```

## Sizing instincts

- If the DELIVERS sentence needs the word "and" twice, it's two tickets.
- Prefactoring ("make the change easy, then make the easy change") is its own ticket, landed first.
- A ticket that can't be demoed isn't a ticket — it's a fragment of one. Find the slice that shows.

## The wide-change exception, worked

Renaming a field used in 400 places can't ship as one green vertical slice. Run **expand → migrate → contract**:

1. **Expand** — add the new form beside the old. Nothing breaks; ship it.
2. **Migrate** — move callers over in batches (per folder, per package), each batch its own ticket blocked by the expand, each landing green because the old form still exists.
3. **Contract** — delete the old form in a final ticket blocked by every migrate batch.

If even batches can't stay green alone, keep the same sequence on a shared integration branch, and promise green only at the final integrate-and-verify ticket — but treat that as the exception's exception, and say so in the plan.
