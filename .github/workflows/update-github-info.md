---
name: update-github-info
description: Draft website updates for Mona's GitHub Info site from official GitHub sources.
on:
  workflow_dispatch:
  schedule:
    - cron: '17 9 * * *'
tools:
  edit:
  web-fetch:
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
network:
  allowed:
    - github.com
    - github.blog
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before making changes.

Use the following sources and read them carefully before drafting updates:
- `notes/mona-notes.md`
- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/

Read external public guidance with web-fetch and use that information to produce concise, practical updates for readers.

For repository guidance or reference files, use GitHub repository API tools instead of terminal, CLI, or sandboxed commands.

Update `site/content/github-info.md` with short, useful summaries that reflect current GitHub guidance and the tone in Mona's notes. Include source context whenever content is grounded in the GitHub Blog or GitHub Changelog.

Open a pull request for Mona to review. Use `safe-outputs` and `create-pull-request` so the agent can propose changes without writing directly to `main`. The pull request should be clearly framed as a GitHub Info update and should be ready for Mona to review before publishing.

Do not write directly to `main`; rely on `safe-outputs` with `create-pull-request` and a pull request workflow for review.

The workflow should be scheduled daily and also support manual runs through `workflow_dispatch`.
