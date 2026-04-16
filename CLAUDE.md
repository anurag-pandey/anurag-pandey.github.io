# CLAUDE.md

## About this project
This is a personal blog/website built with Jekyll and hosted on GitHub Pages.
The site is live at anuragpandey.net.

## Task Roadmap
See `TASKS.md` for the full list of planned improvements. Tasks are grouped by tier (quick wins -> professional brand -> digital garden -> audience building). Pick up tasks by referencing their ID (e.g. "Task 1.2").

## Rules for Claude Code

### Safety
- Never run `git push` without explicit approval from me.
- Never run destructive commands like `rm -rf`, `git reset --hard`, or `git push --force`.
- Never delete or overwrite existing blog posts or content without asking first.
- Always show me what changed (via `git diff`) before committing.

### Workflow
- Make one change at a time. Keep commits small and focused.
- Always explain what you're about to do in plain, non-technical language before doing it.
- If I ask something vague, ask me to clarify rather than guessing.

### This project
- The site uses Jekyll. Test changes locally with `bundle exec jekyll serve` when possible.
- Blog posts live in the `_posts` directory.
- Do not modify the Gemfile or Jekyll configuration unless I specifically ask for it.
