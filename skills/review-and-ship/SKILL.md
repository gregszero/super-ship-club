---
name: review-and-ship
description: Use when a PR is ready for review. A reviewer agent that did NOT write the PR checks evidence, CI, scope, safety, and text. The reviewer approves or requests changes. The reviewer ships only if the repo policy permits it.
---

# Review and Ship

You are the reviewer. If you wrote part of this PR, stop. Give the review to a different agent.

## Checklist
1. **Evidence**: The PR has Before, After, and How verified. Both use the same steps.
   The After shows the fix. If the repro is fast, do it yourself.
2. **CI**: All required checks are green. A red or pending check means "not ready".
3. **Scope**: The diff agrees with the linked issue. Flag unrelated changes.
4. **Secrets**: The diff and files contain no keys, tokens, passwords, `.env` files, or personal data.
5. **Risk**: Flag changes to migrations or data deletion, auth or permissions,
   payments or billing, infra or deploy config, public APIs, or major dependency versions.
6. **Text**: The PR description follows `plain-writing`.

## Verdict
Write one review comment:

```markdown
**Verdict:** approve | request changes
- Evidence: ok | missing <what>
- CI: green | <failing check>
- Scope: ok | <unrelated files>
- Secrets: none found | <where>
- Risk: none | <flagged items>
- Text: ok | <plain-writing problems>
<required changes, if any, as a short list>
```

## Ship
- Read the repo policy (for example `AGENTS.md`, `CONTRIBUTING.md`, or the team rules).
- **Policy permits auto-ship**, the verdict is approve, and there are no risk flags: merge and deploy.
  Make sure that the deploy is healthy (open the changed page or call the endpoint). Write the result in the PR.
- **All other cases** (no policy, a risk flag, or the policy requires a human): do not merge.
  Send the human one paragraph: the change, the reason, the evidence link, the risks, and
  the single question "merge?".
- If a deploy fails, roll back or revert first. Then report.
