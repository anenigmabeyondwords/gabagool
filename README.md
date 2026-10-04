# gabagool

Consulting services for your agent. Don't ask questions.

An output style for Claude Code that makes Claude talk like the guys from North Jersey. Same engineering, different accent. Your code, commands and commit messages stay clean. Only the talking changes.

## Install

```
/plugin marketplace add anenigmabeyondwords/gabagool
/plugin install gabagool@gabagool
```

Then pick the style:

```
/output-style
```

and choose **Gabagool**. In the desktop app, set `"outputStyle"` in `.claude/settings.local.json` or `~/.claude/settings.json` to the name shown in that list.

## Try it locally

```
claude --plugin-dir /path/to/gabagool
```

## What it does

- Speaks the dialect instead of decorating a normal reply with it. The sound, grammar, words, conversational moves and character voices are built from a full read of every episode plus word counts over the whole corpus, with real frequencies, not from memory. Nothing in the style file about how they talk was written by hand.
- Name a character and it stays in that voice.
- Bent idioms (Pandora's lunchbox) are on by default. Sound-alike malapropisms are off; `/gabagool:malapropisms on` turns them on for the session, and `off` turns them back off.
- Describes software work (bugs, tech debt, reviews, dead code, outages) in terms the show's own lexicon contains.
- Keeps everything you copy (code, commands, paths, errors) exact and plain.
- Keeps commits, comments and docs professional unless you ask otherwise.
- Drops the bit and talks straight before anything destructive.

## Not affiliated

A fan project. Not affiliated with HBO, David Chase, or anyone from the show. All lines are original.

## License

MIT

## Built from the show

The style comes from a full read of every episode. A speaker-labeled copy of the episodes (the audio split by voice, then named) measured which habits the whole cast shares and which belong to one character. A second read collected the show's comic engines: mob gravity over trivial things, grievances kept like a ledger, deadpan after disaster, cozy euphemism, therapy-speak in the wrong mouth and confident malapropisms. Public commentary from critics, the writers, linguists and fans set which of those traits people actually hear as the show. Three competing versions of the voice were tested on real coding prompts, judged blind, and the winner was picked in a blind taste test. The four reference files in `skills/sopranos-voice/references/` (a lexicon, a grammar, a discourse guide and character profiles with measured numbers) are written in original words with no quoted dialogue: the only words taken from the show are single terms and expressions of three words or fewer, and every example sentence is invented. The `sopranos-voice` skill points Claude at them when it needs a particular character's voice or more vocabulary than the style file carries.
