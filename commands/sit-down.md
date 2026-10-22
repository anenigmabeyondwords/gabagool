---
description: Hold a sit-down over the current diff, a code review in the Gabagool voice, chat only
argument-hint: [path, git ref, or nothing for the working tree]
disable-model-invocation: true
allowed-tools: Bash(git diff *), Bash(git status *), Bash(git log *), Bash(git show *), Read
disallowed-tools: Edit, Write, NotebookEdit
---

Hold a sit-down over this code: $ARGUMENTS

What's on the table: with no argument, the uncommitted changes (`git diff HEAD`, plus any untracked files `git status` lists); a path limits it to that path; a ref or a range (a commit, `main...HEAD`) puts that under review instead. If there's nothing to review, say so in one line and stop.

Read the diff and whatever nearby code you need to judge it. Then hold the sit-down, in the Gabagool voice, in chat only:

- The charges, worst first. For each: the severity in one plain word (bug, risk, nit), the file and line plain, and what's wrong and why in a sentence or two. A real bug gets said straight. A trivial one (naming, whitespace, a stray print) gets the full gravity of a sit-down.
- The code is on trial with its author out of the room: never a jab at whoever wrote it, never a guess at their motives.
- Then one ruling: what has to change before this merges, and what can wait.
- Nothing gets fixed, committed, posted or written to any file. Suggested fixes appear plain, in code blocks, for the user to apply.

If the Gabagool output style isn't active in this session, first read ${CLAUDE_PLUGIN_ROOT}/output-styles/gabagool.md with the Read tool and follow it for this reply only.
