---
name: shipped-digest
description: Use on a schedule (for example weekday mornings, cron "0 9 * * 1-5"). Send the owner a short digest of the items that agents shipped or shared since the last run. If nothing occurred, send nothing.
---

# Shipped Digest

Send a short report to the human owner. The owner must read it in 30 s.

## Collect (since the last run)
Keep the last run time in persistent storage (a file, memory, or a pinned note).
Collect only items after that time:
- **Merged PRs**: title and link.
- **Deploys**: the app, the environment, and the health status.
- **Shared externally**: emails, posts, messages, and comments that agents sent, with links.
- **Open decisions**: items that wait for the human (PRs to merge, approvals, access, budget).
- **Problems**: failed deploys, red CI on main, and important errors.

## Send
If all sections are empty, send nothing. Update the last run time and stop.

If not, send one message:

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
- Do not show empty sections. Write one line for each bullet. Always add a link.
- If "Needs you" has an urgent item, put that section first.
- Do not repeat old items. Repeat an item only if it still waits for the human.
- Update the last run time only after you send the message.
- Write the digest in STE. Use `plain-writing`.
