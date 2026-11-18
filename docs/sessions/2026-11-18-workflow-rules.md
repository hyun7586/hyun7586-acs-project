# Session: Branch, commit, PR and session-log rules (2026-11-18)

- Agent / model: Claude Code 2.1.311 / claude-opus-5-5
- Branch / PR: `docs/workflow-rules` / #2

## My requests
1. Propose a branch / commit / PR strategy based on what AI engineers and developers commonly use in practice.
2. Show one full example (branch, commit, PR) using the README typo/divider fix, before writing any rules.
3. Commit messages: list the work as bullet points for readability.
4. Keep the `Co-Authored-By` trailer **with** the email, so the agent shows as a co-author on GitHub. AI work must not be hidden.
5. Keep a session log for every agent session: what I asked and how, what the agent did, what it missed, and the result.
6. Write "My requests" in English, even when I prompt in Korean; the agent translates my requests when it writes the log.
7. In each PR, add a short summary of my requests and what the agent did, with a direct link to the session log.
8. Open PRs only; I merge them myself. Put the README fix in its own PR, and the rules + templates + this log in a second PR.

## What the agent did
- Compared common strategies (GitHub Flow, trunk-based, Git Flow) and recommended GitHub Flow with one branch per goal.
- Recommended Conventional Commits, a PR template, and merge commits instead of squash, so the graded commit history is kept.
- Wrote `docs/CONTRIBUTING.md`, `.github/pull_request_template.md`, `docs/sessions/_template.md` and this log.
- Opened PR #1 (README fix) and this PR.

## What it missed / got wrong
- Proposed putting all three changes into one PR; I asked to split them.
- Its first PR example showed the session-log path as plain text, not a clickable link; I asked for a direct link (now a full URL on `main`).

## My corrections
- Bullet-point commit bodies, co-author email kept, English request logs, session-log link in every PR.
- README fix as a separate PR; I merge PRs myself.

## Result
- Workflow rules and templates are ready for review in this PR.
