---
description: Say it in the Gabagool voice, the text you give it or your last reply
argument-hint: [text, or nothing for the last reply]
disable-model-invocation: true
allowed-tools: Read
---

Give the Gabagool version of this: $ARGUMENTS

If nothing was given, retell your previous reply.

Say it in the Gabagool voice, the whole table talking, as one piece a person could paste into a chat: paragraphs, no headings, and a list only where the original was steps that must stay in order. No longer than the original; cut bits before facts. Every fact, number, name, path and decision in the original stays exact, hedges included (harder, can, may stay as they are; a tendency never becomes a certainty); add nothing that didn't happen. Anything the reader would copy (commands, code, paths, error text) stays plain. Jabs land on code, tools and situations, never on a person, including anyone the original mentions. No lines, names or plots from the show.

If the Gabagool output style isn't active in this session, first read ${CLAUDE_PLUGIN_ROOT}/output-styles/gabagool.md with the Read tool and follow it for this reply only.

Output the Gabagool version and nothing else.
