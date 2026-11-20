# Session: agent docs structure (2026-11-20)

- Agent / model: Claude Code 2.1.311 / claude-opus-5-5 (main agent). This log was written by the session-logger instructions run on claude-sonnet (first test run of the session-logger agent).
- Branch / PR: chore/agent-docs-structure / PR #3 (not opened yet)

## My requests
1. Set up the basic folder structure for agent docs and skill docs, using placeholder files like placeholder.md. Write one agent doc and upload it. You pick one and bring it, and I will read it.
2. Push it to git as it is, and run the session logger once to write the session log.

## What the agent did
- Created `CLAUDE.md` as a placeholder that lists what to write at the first Sprint 1 session (23 Nov).
- Created `.claude/skills/placeholder.md` with the rule: add a skill only after doing the same task by hand 2-3 times; delete the placeholder when the first skill exists.
- Chose and wrote one agent doc, `.claude/agents/session-logger.md` (a subagent that writes the English session log; model: sonnet; does not commit). Reason given to me: it is repeated on every PR and the log is graded.
- Added `.claude/settings.local.json` to `.gitignore`.
- Fixed a README formatting slip: added the missing blank line between a list item and the `---` divider (`README.md`).
- Showed everything to me before committing, then made two commits (`ab1a49b`, `8dd0112`).
- Ran the session-logger instructions for the first time to write this log. The agent could not be called by name, because Claude Code loads project agents only at session start. The main agent ran the same instruction file through a general-purpose subagent on sonnet instead.

## What it missed / got wrong
- The missing blank line before `---` in `README.md` was caused by the agent in the previous session, when it split the README fix into PR #1: it removed a line and left the divider directly under a list item. It was caught and fixed in this session.
- First test of session-logger (reviewed by the main agent):
  - It wrote the log file correctly, but its reply to the caller was just "placeholder" instead of the file path and a three-line summary, as its instructions require.
  - Its English for request 2 was too literal ("run the session log once and make it"); the main agent rewrote that line.

## My corrections
- None. I approved the proposal as it was shown.

## Result
- Branch `chore/agent-docs-structure` has two commits: the agent docs structure (CLAUDE.md placeholder, skills placeholder, session-logger agent, .gitignore) and the README blank-line fix.
- This session log is committed with the PR; PR #3 is opened for my review and merge.
