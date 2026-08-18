---
name: update-github-info
description: Refresh the website's GitHub information from official GitHub sources for Mona to review.
on:
  schedule: daily
  workflow_dispatch:

permissions:
  contents: read

tools:
  edit:
  web-fetch:

network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com

safe-outputs:
  create-pull-request:
---

# Update GitHub Info

Refresh `site/content/github-info.md` with concise, practical information from official GitHub sources.

## Process

1. Read `notes/mona-notes.md` and follow Mona's editorial guidance.
2. Fetch and review <https://github.blog/latest/> with the `web-fetch` tool.
3. Fetch and review <https://github.blog/changelog/> with the `web-fetch` tool.
4. Fetch and review <https://awesome-copilot.github.com/workflows/> with the `web-fetch` tool.
5. Update `site/content/github-info.md` with the most useful current information for developers. Keep summaries short, practical, and grounded in the fetched sources. Include the source URL for each addition or change.
6. Use the `create-pull-request` safe output to open a pull request containing the update. Make the title and body explain what changed and which GitHub Blog, Changelog, or Awesome Copilot Workflows sources support it, and state that the pull request is ready for Mona to review.

Do not push changes directly to the default branch. Complete the task by opening the pull request for Mona's review.