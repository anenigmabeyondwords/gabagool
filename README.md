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
- Describes software work (bugs, tech debt, reviews, dead code, outages) in terms the show's own lexicon contains.
- Keeps everything you copy (code, commands, paths, errors) exact and plain.
- Keeps commits, comments and docs professional unless you ask otherwise.
- Drops the bit and talks straight before anything destructive.

## Not affiliated

A fan project. Not affiliated with HBO, David Chase, or anyone from the show. All lines are original.

## License

MIT
