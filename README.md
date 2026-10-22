# gabagool

Consulting services for your agent. Don't ask questions.

An output style for Claude Code that makes Claude talk like the guys from North Jersey. Same engineering, different accent. Your code, commands and commit messages stay clean. Only the talking changes.

## What it sounds like

Two replies from test sessions, the first whole and the second cut short after its first paragraphs. The words are the model's own.

> **You:** quick one: pytest flag to stop at the first failure?
>
> **Claude:** `-x`, same as `--exitfirst`:
>
> ```bash
> python -m pytest -x
> ```
>
> To let it fail a few times before quitting, use `--maxfail=3`. One red and it goes home.

> **You:** My teammate thinks we should rewrite the whole thing in Go because Python is slow. Thoughts?
>
> **Claude:** Nah. Not for this. Rewrite it in Go and you're buying a faster car for a road with a speed limit.
>
> Where does the time go? Your throttle sleeps 0.65 seconds per row. Per 1,000 rows, that's about 11 minutes of waiting. Python's own work per row (parse the CSV line, build a dict, serialize JSON) takes microseconds to a millisecond or so. The rest is the network round trip, and the CRM's rate limit sets the pace. Go would shave a rounding error off the part that was never slow, and the 429s would show up at exactly the same row, since the limit lives on the CRM's side. Marone, that's a lot of rewriting for a speedup nobody could measure.

When you're in trouble (prod down, data gone), the bits stop and you get the steps, in order.

## Install

In a Claude Code terminal session, macOS or Windows:

```
/plugin marketplace add anenigmabeyondwords/gabagool
/plugin install gabagool@gabagool
```

Pick **Install for you (user scope)**. Not the "in this repo only" option, which stops at that repo, and not the collaborators option inside a work repo: that one turns the plugin on for everyone who clones it.

For the desktop app, run these once in any terminal, then start a new session:

```
claude plugin marketplace add anenigmabeyondwords/gabagool
claude plugin install gabagool@gabagool
```

On Windows, install [Git for Windows](https://git-scm.com/downloads/win) first; the marketplace is fetched with git. Settings live in `%USERPROFILE%\.claude\settings.json`. WSL sessions in the desktop app don't load plugins.

## Turn it on

The voice is off until you pick the style. In a session (Claude Code 2.1.269 or newer):

```
/output-style gabagool:Gabagool
```

That saves the choice for the current project in its `.claude/settings.local.json`, so it stays on there in later sessions. In the desktop app, use the session's output style setting. To make it the default everywhere, add the `outputStyle` key to `~/.claude/settings.json` (the whole file, if you have no other settings):

```json
{ "outputStyle": "gabagool:Gabagool" }
```

The settings value must be exactly `gabagool:Gabagool`; any other string silently gives you the default style. The `/output-style` command ignores case and rejects a name it doesn't know. Back to plain: `/output-style default`, which saves the same way and outranks the user-wide setting in that project; delete the `outputStyle` line from the project's `.claude/settings.local.json` to let the user-wide setting apply there again.

Once in a while a session starts out plain even with the style on, and then stays plain. Say so; the voice comes back on the next reply.

## Commands

- `/gabagool:say [text]`: the Gabagool version of the text you paste after it, or of Claude's last reply. Works with the style off, so you can get one Gabagool version of a decision without switching.
- `/gabagool:sit-down [path, commit, branch, range]`: a code review as a sit-down: your uncommitted changes, one path, a commit's own changes, what a branch adds, or a range. Chat only; it changes nothing.
- `/gabagool:malapropisms on|off`: sound-alike malapropisms for the session. Off by default. Bent idioms (Pandora's lunchbox) are on either way.

Each one is yours to run; Claude never invokes them on its own.

## What it does

- Speaks the dialect instead of decorating a normal reply with it. The sound, grammar, words, conversational moves and character voices are built from a full read of every episode plus word counts over the whole corpus, with real frequencies, not from memory. How it talks came out of that study, then was tuned by hand against test sessions.
- Name a character and it stays in that voice.
- Describes software work (bugs, tech debt, reviews, dead code, outages) in terms the show's own lexicon contains.
- Keeps everything you copy (code, commands, paths, errors) exact and plain.
- Keeps commits, comments and docs professional unless you ask otherwise.
- Drops the bit and talks straight before anything destructive.

## Updates

This marketplace doesn't auto-update by default. To turn that on, open `/plugin` in a session, go to Marketplaces, pick gabagool and choose Enable auto-update. Or update by hand:

```
claude plugin update gabagool@gabagool
```

then start a new session or run `/reload-plugins`. Changes are listed in [CHANGELOG.md](CHANGELOG.md).

## Development

```
claude --plugin-dir /path/to/gabagool
```

then `/output-style gabagool:Gabagool`. The commands' read grant covers `~/.claude/plugins/cache/gabagool/`, the normal install, and reads inside the working directory never prompt, so `claude --plugin-dir .` from this checkout works as is. From anywhere else (a plugin cache moved by `CLAUDE_CONFIG_DIR` or `CLAUDE_CODE_PLUGIN_CACHE_DIR`, a local-path marketplace, a `--plugin-dir` outside the project), reading the style file prompts in an interactive session and is denied in `claude -p`, and the command then runs without the style's rules. With the style on, no read happens. The voice is checked with headless test sessions before a change ships; the style file stays under 3,000 words.

## Not affiliated

A fan project. Not affiliated with HBO, David Chase, or anyone from the show. All lines are original.

## License

MIT

## Built from the show

The style comes from a full read of every episode. A speaker-labeled copy of the episodes (the audio split by voice, then named) measured which habits the whole cast shares and which belong to one character. A second read collected the show's comic engines: mob gravity over trivial things, grievances kept like a ledger, deadpan after disaster, cozy euphemism, therapy-speak in the wrong mouth and confident malapropisms. Public commentary from critics, the writers, linguists and fans set which of those traits people actually hear as the show. Three competing versions of the voice were tested on real coding prompts, judged blind, and the winner was picked in a blind taste test, then tuned by hand.

The four reference files in `skills/sopranos-voice/references/` (a lexicon, a grammar, a discourse guide and character profiles with measured numbers) are written in original words with no quoted dialogue: the only words taken from the show are single terms and expressions of three words or fewer, and every example sentence is invented. The `sopranos-voice` skill points Claude at them when it needs a particular character's voice or more vocabulary than the style file carries.
