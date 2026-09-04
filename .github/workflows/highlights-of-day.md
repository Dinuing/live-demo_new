---
description: Add one unused GitHub Agentic Workflows FAQ entry to the daily updates for the current UTC date.
intent: Keep the site's daily FAQ highlights fresh by selecting one unanswered question from the official FAQ and appending it to the matching day's update.
on:
  schedule: every 6 hours
  workflow_dispatch:
permissions:
  contents: read
  issues: read
  pull-requests: read
  copilot-requests: write
network:
  allowed:
    - github.github.com
tools:
  github:
    mode: gh-proxy
    toolsets: [default]
  edit:
  web-fetch:
safe-outputs:
  create-pull-request:
    allowed-files:
      - index.html
    max: 1
engine: copilot
---

# Highlights of the Day

## Task

Fetch the GitHub Agentic Workflows FAQ at https://github.github.com/gh-aw/reference/faq/.

Choose exactly one FAQ question that is not already represented in `index.html`.

Use the workflow run's UTC date and match the existing Daily Updates pattern in `index.html`:

- use the same date wording style as the existing entries
- reuse the matching dialog if that date already has a placeholder dialog
- otherwise add a matching navigation control and dialog
- preserve all existing updates and never duplicate dates, buttons, dialogs, or FAQs
- if the current date's dialog already contains a FAQ, or no unused FAQ remains, make no change

The update must use the existing HTML structure, ID conventions, date wording, and styling. Keep the question concise and the answer brief, accurate, and grounded in the official FAQ.

## Output requirements

- Update `index.html` only.
- Keep all existing content intact.
- Add a new Daily Updates entry for the current UTC date when appropriate.
- Add a matching accessible dialog with the question and answer.
- If no valid update is required, do not change the file.

## Safe outputs

Create a pull request that modifies only `index.html` and respects the configured `max: 1` limit.

## Validation

Run `gh aw validate highlights-of-day` before completing the workflow. Do not compile the workflow.
