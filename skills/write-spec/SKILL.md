---
name: write-spec
description: Use when a request, bug report, agent finding, analytics signal, or customer message should become work. Turns it into one deduplicated GitHub issue, with priority and labels, that a dev agent can act on without asking questions.
---

# Write Spec

Humans and agents (PM, QA, support, ads, social) can file issues. Same rules for both.

## 1. Dedupe first
- `gh issue list --state open --search "<keywords>"`, then check recently closed ones too.
- Already filed? Comment the new evidence on that issue instead. Don't open a new one.
- One issue per problem. Split bundled requests.

## 2. Write the issue

```markdown
## Problem
<who is affected, what goes wrong, one paragraph>

## Evidence / Repro
1. <URL or command, account/state, inputs>
2. Actual: <what happens>
<links, screenshots, logs, metric + time window, source message>

## Expected
<what should happen>

## Acceptance criteria
- [ ] <observable, testable outcome>
- [ ] <...>

## Out of scope
- <what not to touch>
```

- Unclear repro? Write what is known and label `needs-repro`. Don't invent steps.
- Strip secrets and customer personal data. Quote messages without names or contact details.

## 3. Priority (pick one)
- **P0**: broken checkout/payments, data loss, outage, security.
- **P1**: major user-facing breakage or a blocked main flow.
- **P2**: normal bug or feature.
- **P3**: nice to have.

## 4. Labels
- Type: `bug` | `feature` | `chore` | `content`
- Area: `area:<name>` (e.g. `area:checkout`, `area:auth`)
- Priority: `priority:P0`..`priority:P3`
- `agent-created` when an agent filed it

## 5. Create

```bash
gh issue create --title "<short, specific title>" --body-file spec.md \
  --label bug --label area:checkout --label priority:P1 --label agent-created
```

Missing labels: `gh label create <name>` once.

## 6. After
- **P0**: ping the lead and the human now, with the issue link. Don't wait for the digest.
- Others: report the link to your lead and stop. The digest picks it up.
