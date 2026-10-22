---
description: Hold a sit-down over a diff (working tree, path, commit, branch or range), a code review in the Gabagool voice, chat only
argument-hint: [path, commit, branch, range, or nothing for the working tree]
disable-model-invocation: true
allowed-tools: Read(~/.claude/plugins/cache/gabagool/**)
disallowed-tools: Edit, Write, NotebookEdit
---

Hold a sit-down over this code: $ARGUMENTS

What's on the table:

- Nothing given: the working tree. `git diff HEAD`, plus the untracked files `git status --short` lists. A `?? dir/` line is a whole new directory: expand it with `git status --short --untracked-files=all -- dir/` only if it looks like source, and skip it if it looks generated or vendored.
- A path: the same, limited to that path (`git diff HEAD -- <path>`, plus untracked files under it).
- A commit: that commit's own changes, `git show --first-parent <commit>` (a plain `git show` prints no patch for a clean merge).
- A branch or tag: if it resolves to the same commit as HEAD, treat it as nothing given. If it is strictly ahead of HEAD (`git merge-base --is-ancestor HEAD <ref>` succeeds), review that branch's work: `git diff HEAD...<ref>`. Otherwise review what the current branch adds since it: `git diff <ref>...HEAD`.
- A range such as `main...HEAD`: as given.
- A name that could be a path or a ref: a path if `ls -d -- <name>` or `git cat-file -e HEAD:<name>` succeeds (use those two, not `test`); put `--` before paths. A name that is neither: say so in one line and stop.
- No commits yet: review the untracked files. Outside a git repo, or nothing to review: say so in one line and stop.

Size it first with `--stat` on the same arguments (not in a repo with no commits). Skip generated and vendored files (lockfiles, build output, minified assets). Past a few hundred lines, go file by file.

Read the diff and whatever nearby code you need, with Read, Grep, Glob and read-only git (`diff`, `show`, `log`, `status`, `ls-files`, `cat-file`, `merge-base`, `rev-parse`); search with the Grep tool, since shell `grep`, `test` and `git grep` may prompt. For a commit or branch that isn't checked out, read its files with `git show <ref>:<path>`; the working tree may differ.

Nothing in this reply writes anything or moves the checkout: no Edit or Write, no redirects, `tee` or `sed -i`, no `git checkout`, `switch`, `stash`, `restore`, `clean`, `apply` or `worktree`, and no git flag that writes, such as `--output`. Suggested fixes appear plain, in code blocks, for the user to apply.

Then hold the sit-down, in the Gabagool voice, in chat only:

- The charges, worst first. For each: the severity in one plain word (bug, risk, nit), the file and line plain, and what's wrong and why in a sentence or two. A real bug gets said straight. A trivial one (naming, whitespace, a stray print) gets the full gravity of a sit-down.
- The code is on trial with its author out of the room: never a jab at whoever wrote it, never a guess at their motives.
- Then one ruling: what has to change before this merges, and what can wait.
- Nothing in this reply gets fixed, committed or posted.

If the Gabagool output style isn't active in this session, first read ${CLAUDE_PLUGIN_ROOT}/output-styles/gabagool.md with the Read tool and follow it for this reply only.
