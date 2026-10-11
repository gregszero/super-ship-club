---
name: simple-code
description: Use when you do the work for an issue. Write the simplest change that solves it. Write tests for the real cases in the issue.
---
# Simple code

Solve the issue with the smallest and clearest change that works. Test the behavior that the issue makes important. Do not test every line.

## Before you write code
1. Read the issue and its acceptance criteria. You must prove each criterion.
2. Reproduce the issue first (see `reproduce-before-after`). The repro is your first test.
3. Find how the codebase solves similar problems. Use the same pattern.

## Write the change
- Change the minimum number of files and lines that meet the criteria. Do not refactor other code.
- Write simple, readable code. Do not write clever code. Use clear names, not comments.
- Do not add a dependency, abstraction, or config option unless the issue needs it.
- Do not write code for possible future cases. Delete dead code in the parts that you change.
- If the simple fix seems wrong, stop. Write the reason on the issue. Do not increase the scope.

## Tests
Test real behavior. Do not aim for a coverage percentage.
- Write one test for each acceptance criterion. Give the test the name of the criterion.
- Write a regression test from the repro. It must fail before the fix and pass after the fix.
- Test edge cases only when the issue, the repro, or production data shows them (for example empty input, wrong user, duplicate submit).
- Test through public behavior (request, page, command). Do not test private internals.
- Do not write tests for simple glue code, framework code, or copy changes.
- Make tests fast and deterministic. Do not use the real network. Do not use sleeps.

## Done when
- Each acceptance criterion has a passing test, or a written reason why you cannot test it.
- The full test suite and the linters pass locally and in CI.
- A reader can read the diff in 2 min. If not, split it.
- The PR description gives the change, the reason it is the simplest option, the tests for each criterion, and the Before / After evidence. Write it in STE (`plain-writing`).
