---
name: write-spec
description: Use when a request, bug report, agent finding, analytics signal, or customer message must become work. Make one GitHub issue with no duplicate, a priority, and labels. A dev agent must be able to do the work without questions.
---

# Write Spec

Humans and agents (PM, QA, support, ads, social) can file issues. The same rules apply to all.

## 1. Find duplicates first
- Run `gh issue list --state open --search "<keywords>"`. Then examine recently closed issues.
- If the issue exists, add the new evidence as a comment on it. Do not open a new issue.
- Write one issue for each problem. Split a request that has many problems.

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

- Write the issue text and the acceptance criteria in STE. Use `plain-writing`.
- If the repro is not clear, write the known facts. Add the label `needs-repro`. Do not invent steps.
- Remove secrets and customer personal data. Quote messages without names or contact data.

## 3. Priority (select one)
- **P0**: checkout or payments broken, data loss, outage, security.
- **P1**: large user-facing failure, or the main flow is blocked.
- **P2**: usual bug or feature.
- **P3**: optional improvement.

## 4. Labels
- Type: `bug` | `feature` | `chore` | `content`
- Area: `area:<name>` (for example `area:checkout`, `area:auth`)
- Priority: `priority:P0`..`priority:P3`
- `agent-created` if an agent filed the issue

## 5. Create

```bash
gh issue create --title "<short, specific title>" --body-file spec.md \
  --label bug --label area:checkout --label priority:P1 --label agent-created
```

If a label does not exist, run `gh label create <name>` one time.

## 6. After
- **P0**: Send the issue link to the lead and the human now. Do not wait for the digest.
- Other priorities: Send the link to your lead and stop. The digest shows the issue.
