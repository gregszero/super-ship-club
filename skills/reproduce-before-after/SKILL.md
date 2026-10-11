---
name: reproduce-before-after
description: Use when fixing a bug or building a feature that changes behavior. Reproduce the BEFORE state first, capture the AFTER with the same steps, and put both in the PR.
---

# Reproduce Before / After

No evidence, no PR.

## 1. Reproduce BEFORE touching code
- Write exact repro steps: URL or command, inputs, account/state, expected vs actual.
- Capture proof of the current state, in order of preference:
  1. A failing automated test that encodes the bug or missing feature.
  2. A screenshot or short recording (UI changes).
  3. Command output or logs (CLI/API changes).
- Save artifacts with clear names: `before-<slug>.png`, `before-<slug>.log`.

**If you cannot reproduce it: stop.** Do not guess at a fix. Report what you tried,
what you saw, and what you need (data, access, clearer steps).

## 2. Make the change
- Keep the diff scoped to the issue. No drive-by refactors.

## 3. Capture AFTER with the SAME steps
- Re-run the identical steps, same inputs and state.
- The failing test now passes; the screenshot/output shows the fixed behavior.
- Save as `after-<slug>.*`. Check nothing nearby regressed.

## 4. Open the PR with this section

```markdown
## Before
<steps> + <screenshot / failing test / output>

## After
<same steps> + <screenshot / passing test / output>

## How verified
- Tests: <command> -> <result>
- Manual: <what you clicked/ran, where (local/staging)>
- Not verified: <anything you couldn't check, and why>
```

## Rules
- Before and After must use the same steps; otherwise the comparison is meaningless.
- Never fake or stage evidence. Mark anything unverified as unverified.
- Strip secrets, tokens, and personal data from screenshots and logs.
