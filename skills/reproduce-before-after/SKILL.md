---
name: reproduce-before-after
description: Use when you fix a bug or make a feature that changes behavior. Reproduce the BEFORE state first. Record the AFTER state with the same steps. Put both in the PR.
---

# Reproduce Before / After

Do not open a PR without evidence.

## 1. Reproduce BEFORE you change code
- Write the exact repro steps: URL or command, inputs, account and state, expected result, actual result.
- Record evidence of the current state. Use this order of preference:
  1. A failing automated test that shows the bug or the missing feature.
  2. A screenshot or a short recording (for UI changes).
  3. Command output or logs (for CLI and API changes).
- Give the files clear names: `before-<slug>.png`, `before-<slug>.log`.

**If you cannot reproduce it, stop.** Do not guess a fix. Report the steps you did,
the result you saw, and the item you need (data, access, or clearer steps).

## 2. Make the change
- Change only the code that the issue needs. Do not refactor other code.

## 3. Record AFTER with the SAME steps
- Do the same steps again. Use the same inputs and the same state.
- Make sure that the failing test passes. Make sure that the screenshot or output shows the correct behavior.
- Save the files as `after-<slug>.*`. Make sure that related behavior did not break.

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
- Use the same steps for Before and After. Different steps make the comparison useless.
- Do not fake evidence. Mark all unverified items as "unverified".
- Remove secrets, tokens, and personal data from screenshots and logs.
