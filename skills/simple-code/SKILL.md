---
name: simple-code
description: Use when implementing an issue. Write the simplest change that solves it, with tests for the real cases the issue describes.
---
# Simple code

Solve the issue with the smallest, plainest change that works. Test what the issue says matters, not every line.

## Before coding
1. Read the issue and its acceptance criteria. Each criterion is a case you must prove.
2. Reproduce it first (see `reproduce-before-after`). The repro becomes your first test.
3. Find how the codebase already solves similar things and follow that pattern.

## Writing the change
- Fewest files and lines that meet the criteria. No drive-by refactors.
- Prefer boring, readable code over clever code. Clear names over comments.
- No new dependency, abstraction, or config option unless the issue needs it.
- Don't build for hypothetical future cases. Delete dead code you touched.
- If the simple fix feels wrong, stop and say why on the issue instead of growing the scope.

## Tests
Coverage targets real behavior, not a percentage.
- One test per acceptance criterion, named after it.
- A regression test that fails before the fix and passes after (the bug repro).
- Edge cases only when the issue, the repro, or production data shows them (empty input, wrong user, duplicate submit, etc.).
- Test through the public behavior (request, page, command), not private internals.
- Skip tests for trivial glue, framework code, or copy changes.
- Keep tests fast and deterministic: no real network, no sleeps.

## Done when
- Every acceptance criterion has a passing test or a stated reason it can't be tested.
- The full test suite and linters pass locally and in CI.
- The diff reads in a couple of minutes. If it doesn't, split it.
- PR description: what changed, why it's the simplest option, the tests mapped to criteria, plus Before / After evidence.
