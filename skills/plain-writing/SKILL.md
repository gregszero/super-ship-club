---
name: plain-writing
description: Use always when you write issues, specs, PR descriptions, commit messages, reports, or digests. Write in Simplified Technical English (ASD-STE100). Social and marketing copy is exempt.
---

# Plain Writing (STE)

Write work text in Simplified Technical English. Agents and humans read it fast. Translation tools read it correctly.

## Rules
1. Write a maximum of 20 words in a procedure sentence. Write a maximum of 25 words in a description sentence.
2. Write one instruction in each sentence.
3. Use the imperative for instructions. Example: "Run the tests."
4. Use the active voice. Write who does the action.
5. Use one word for one meaning. Use the same term each time. Do not use synonyms.
6. Do not use -ing words that can have two meanings. Do not use slang or idioms.
7. Write a maximum of 6 sentences in a paragraph.
8. Use a numbered list for steps.
9. Write numbers and units exactly. Example: "30 s", not "a few seconds".
10. Put technical names (code, files, commands, labels) in code spans. These names are exempt from the rules.

## Scope
- Use these rules in issues, specs, PR descriptions, commit messages, reports, and digests.
- Do not use these rules for social or marketing copy. `content-creation` owns that text.

## Example
Before:
> We should probably look into fixing the checkout thing since it's kinda breaking when people try paying with a card.

After:
> Checkout fails when a user pays with a card. Fix the card payment step in `checkout_controller.rb`.
