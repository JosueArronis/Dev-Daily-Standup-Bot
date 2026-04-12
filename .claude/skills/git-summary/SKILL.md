---
name: git-summary
description: >
  Summarizes recent git commits into human-readable bullet points.
  Use when asked to read commit history or summarize what was done recently.
---

# Git Summary Skill

When this skill is triggered, follow these steps:

1. Run `git log --oneline -10` to get the last 10 commits
2. Group commits by type: feat, fix, chore, docs
3. Translate commit messages into plain English
   - 'feat: add user auth' → 'Added user authentication'
   - 'fix: null pointer in payment' → 'Fixed crash in payment flow'
4. Return a bullet list of 3-5 items maximum
5. Ignore merge commits and version bumps
