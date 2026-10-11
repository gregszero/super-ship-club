---
name: shipped-digest
description: Use on a schedule (suggested weekday mornings, cron "0 9 * * 1-5") to send the owner a short digest of what agents shipped or shared since the last run. Stay silent if nothing happened.
---

# Shipped Digest

A short report to the human owner. Read in 30 seconds.

## Gather (since last run)
Store the last run time somewhere persistent (a file, memory, or a pinned note).
Collect only what happened after it:
- **Merged PRs**: title + link.
- **Deploys**: what, where, healthy or not.
- **Shared externally**: emails, posts, messages, comments agents sent, with links.
- **Open decisions**: anything waiting on the human (PRs to merge, approvals, access, budget).
- **Problems**: failed deploys, red CI on main, errors worth knowing.

## Send
If every section is empty: send nothing. Update the last-run time and stop.

Otherwise send one message:

```markdown
**Shipped since <date>**
- <PR title> (<link>)
- Deployed <app> to <env>: healthy

**Shared**
- Email to <who>: <subject> (<link>)

**Needs you**
- <decision>: <one-line context> (<link>)

**Problems**
- <what broke, current state>
```

## Rules
- Omit empty sections. Bullets only, one line each, always with a link.
- Put "Needs you" first if it has anything urgent.
- No restating old items unless they are still waiting on the human.
- Update the last-run time only after the message is sent.
