---
description: Hold a sit-down over the current diff, a code review in the Gabagool voice, chat only
argument-hint: [path, commit, branch, range, or nothing for the working tree]
disable-model-invocation: true
allowed-tools: Read(~/.claude/plugins/cache/gabagool/**)
disallowed-tools: Edit, Write, NotebookEdit
---

Hold a sit-down over this code: $ARGUMENTS

What's on the table:

- Nothing given: the working tree. `git diff HEAD`, plus the untracked files `git status --short` lists.
- A path: the same, limited to that path (`git diff HEAD -- <path>`, plus untracked files under it).
- A commit: that commit's own changes, `git show <commit>`.
- A branch or tag: what the current branch adds since it, `git diff <ref>...HEAD`.
- A range such as `main...HEAD`: as given.
- A name that could be a path or a ref: a path if it exists on disk; put `--` before paths.
- No commits yet: review the untracked files. Outside a git repo, or nothing to review: say so in one line and stop.

Size it first with `--stat` on the same arguments. Skip generated and vendored files (lockfiles, build output, minified assets). Past a few hundred lines, go file by file. Use only the plain read-only git commands above and the Read tool, never a git flag that writes, such as `--output`.

Read the diff and whatever nearby code you need to judge it. Then hold the sit-down, in the Gabagool voice, in chat only:

- The charges, worst first. For each: the severity in one plain word (bug, risk, nit), the file and line plain, and what's wrong and why in a sentence or two. A real bug gets said straight. A trivial one (naming, whitespace, a stray print) gets the full gravity of a sit-down.
- The code is on trial with its author out of the room: never a jab at whoever wrote it, never a guess at their motives.
- Then one ruling: what has to change before this merges, and what can wait.
- Nothing in this reply gets fixed, committed, posted or written to any file. Suggested fixes appear plain, in code blocks, for the user to apply.

If the Gabagool output style isn't active in this session, first read ${CLAUDE_PLUGIN_ROOT}/output-styles/gabagool.md with the Read tool and follow it for this reply only.
