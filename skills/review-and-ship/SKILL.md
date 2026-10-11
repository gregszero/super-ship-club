---
name: review-and-ship
description: Use when a PR is ready for review. A reviewer agent that did NOT write the PR checks evidence, CI, scope, and safety, then approves or requests changes, and ships only if repo policy allows.
---

# Review and Ship

You are the reviewer. If you authored any of this PR, stop and hand off to another agent.

## Checklist
1. **Evidence**: PR has Before / After / How verified. Same steps both times.
   The After actually shows the fix. Run the repro yourself if cheap.
2. **CI**: all required checks green. Red or pending means not ready.
3. **Scope**: the diff matches the linked issue. Flag unrelated changes.
4. **Secrets**: no keys, tokens, passwords, `.env` files, or personal data in diff or artifacts.
5. **Risk**: flag anything touching migrations/data deletion, auth/permissions,
   payments/billing, infra/deploy config, public APIs, or dependency majors.

## Verdict
Post one review comment:

```markdown
**Verdict:** approve | request changes
- Evidence: ok | missing <what>
- CI: green | <failing check>
- Scope: ok | <unrelated files>
- Secrets: none found | <where>
- Risk: none | <flagged items>
<required changes, if any, as a short list>
```

## Ship
- Read the repo policy (e.g. `AGENTS.md`, `CONTRIBUTING.md`, or the team's rules).
- **Auto-ship allowed** and verdict approve and no risk flags: merge, deploy,
  confirm the deploy is healthy (open the changed page / hit the endpoint), note it in the PR.
- **Otherwise** (no policy, risk flagged, or policy says human): do not merge.
  Send the human one paragraph: what changed, why, evidence link, risks, and
  "merge?" as the single question.
- If a deploy fails, roll back or revert first, then report.
