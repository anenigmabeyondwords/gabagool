# Changelog

## 0.3.1 (2026-10-21)

- Commands: narrower permissions. The git grants are gone (a `git diff *` rule also approved `--output=<file>`, which writes; plain read-only git needs no grant), and the Read grant covers only the plugin's own files under the plugin cache, in place of any file.
- `/gabagool:sit-down`: says what each kind of argument reviews (working tree, path, commit, branch, range), handles untracked files, a repo with no commits and a huge diff, and refuses writing git flags.
- `/gabagool:say`: says so and stops when there is no earlier reply to retell.
- README: the second sample is the reply's own first paragraphs, not a rewrite; the install scope names the exact option; the `/output-style` command's behaviour and version floor; a complete settings snippet.

## 0.3.0 (2026-10-21)

- New command `/gabagool:say`: the Gabagool version of the text you give it, or of Claude's last reply. Works with the style off.
- New command `/gabagool:sit-down`: a review of the current diff as a sit-down, chat only.
- Style: the stressed-user opener is a description instead of an example that test sessions repeated word for word, and the commit handover no longer announces that the commit is plain. A flourish line in the sound-alike rule was cut to stay under the word cap.
- README: the exact style name (`gabagool:Gabagool`), desktop app and Windows install, install scope, updates, and two sample replies.

## 0.2.1 (2026-10-04)

- The marks (food, Italian, the minced swear) are asked for at one consistent rate, and food stops once you wave it off.
- `/gabagool:malapropisms` can only be run by you, and asks compaction to keep the setting.
- Character references: each habit listed once; Livia's figures drop a labeling artifact and carry a caveat.
- README provenance lines mention the hand tuning.

## 0.2.0 (2026-10-04)

- The voice rebuilt on the show's comic engines and the habits the whole cast shares, chosen from three blind-tested versions.
- Bent idioms on by default; sound-alike malapropisms off, behind the new `/gabagool:malapropisms on|off`.
- Character references gain measured per-speaker figures and a note on what makes each character funny.

## 0.1.0 (2026-10-03)

- The Gabagool output style.
- The `sopranos-voice` reference skill: lexicon, grammar, discourse and character profiles, built from a full read of the series.
