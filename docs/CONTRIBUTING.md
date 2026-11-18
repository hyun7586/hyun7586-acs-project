# Workflow: branches, commits, PRs, session logs

This project is built mostly by AI agents under my direction. The workflow below keeps a clear record of what I asked, what the agent did, and what I checked.

## Branches (GitHub Flow)

- `main` always works. No direct commits to `main` after the initial commit.
- One short-lived branch per goal or task, merged through a PR.
- Name: `<type>/<short-description>`, with the goal number when there is one.
  - `feat/g1-measure-move`, `fix/rss-timeout`, `docs/readme-format`

## Commits (Conventional Commits)

```
<type>(<scope>): <summary, imperative, ~50 chars>

- <what changed and why>
- <what changed and why>

Co-Authored-By: Claude Opus 5.5 <noreply@anthropic.com>
```

- Types: `feat`, `fix`, `docs`, `test`, `refactor`, `chore`, `eval` (evaluation data and scripts).
- Scope: the goal (`g1` ... `g6`) or the area (`readme`, `data`, `cli`).
- Body: bullet points.
- Every commit made with AI help carries a `Co-Authored-By` trailer with the exact model and its email, so the agent shows as a co-author on GitHub. AI work is never hidden.
- A commit is made only after the check for that goal passes.

## Pull requests

- One PR per goal (or part of a goal). Fill in `.github/pull_request_template.md`.
- The PR contains a short summary of **My requests** and **What the agent did**, and a link to the full session log.
- Merge with a **merge commit** (no squash), so every commit stays in the history. Delete the branch after the merge.

## Session logs

- One file per agent session: `docs/sessions/YYYY-MM-DD-<topic>.md`, from `docs/sessions/_template.md`.
- The log is committed in the same PR as the work.
- Written in English. My prompts may be in Korean; the log records them translated into English, keeping the meaning.
- Records: my requests, what the agent did, what it missed or got wrong, my corrections, the result.
- "What it missed" is never left blank: write "None" if nothing was missed.
