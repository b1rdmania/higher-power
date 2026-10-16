# Higher Power

A Claude Code skill that finds the strongest version of a task, and how to prove it worked. It names the rung above the ask in one line before the work starts.

Based on Felix Rieseberg's post [How to be more ambitious: A tutorial for humans with models](https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/). The four altitudes, the depth questions, and the stories are his.

## Install

```bash
git clone https://github.com/b1rdmania/higher-power ~/.claude/skills/higher-power
```

## Usage

The skill fires on the shape of the task, not on a command. Give Claude Code a task that is outcome-shaped, meeting-shaped, or sits on raw material it has not seen. Before it executes, it says one line:

```
Higher rung: group last month's crashes by root cause and fix the largest cluster, not this one crash. Say the word.
```

Then it does the task as asked. Say the word and it climbs, writes the stronger brief, and runs it. It stops to ask only if the brief would widen the scope you agreed. Say nothing and it continues.

Explicit triggers also work:

```
higher power
be more ambitious
what should I be asking for
```

## What it does

```mermaid
flowchart TD
    A[Task arrives] -- find the ceiling --> B{Rung above it?}
    B -- no --> C[Do the task]
    B -- yes --> D[Name the rung in one line, then do the task]
    D -- "say the word" --> E[Altitude: the goal beyond the goal]
    E --> F[Depth: four questions, rawest material, real instruments]
    F --> G[Range: nouns to verbs, assemble the crew]
    G --> H[Judge: name what outside the model shows it is right]
    H -- stronger brief --> I[Run it. Ask only if scope widens]
```

- Names one rung per thread, in one concrete line, then proceeds as asked. A rung is a better objective or a stronger method in the same scope
- On "say the word", climbs Altitude, Depth, and Range, writes the brief that asks for exactly that, and runs it
- Requires an outside judge for the result. If none exists, it says so instead of inventing one
- Uses the methods of a field, not the voice. It researches like a short seller; it does not write like one

## What it does not do

- Does not offer speed as a rung. Faster is not more ambitious
- Does not change the intent of creative work. It climbs method and research only
- Does not fire after the user writes "bro"
- Does not offer a second rung in a thread after the first was declined

## Always-on line

The skill description makes Claude Code load it when the task fits. To make the check run on every task, add this to `~/.claude/CLAUDE.md`:

```markdown
## Higher Power
Before executing a task that is outcome-shaped, meeting-shaped, or sits on raw material I have not seen, find the ceiling in the ask. If there is a rung above it, name it in one line ("Higher rung: X. Say the word.") and then do the task as asked. A rung is a better objective or a stronger method in the same scope; bigger is not the default. Once per thread; never after "bro"; on creative work change the method, never the intent. The skill `higher-power` has the full method for when the word is said.
```

## Requirements

Claude Code. No MCP servers, keys, or binaries.

## License

MIT
