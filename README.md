# senpai 🎓

**Your agent writes the code. You still learn.**

AI agents write more of our code every day, and many of us feel it: we ship faster, but we understand less. senpai is a skill for Claude Code and Codex that turns your agent into the senior engineer next to you. It still does the work at full speed. After each meaningful change, it adds a 30-second lesson and one question, so you keep growing instead of getting rusty.

## What it looks like

You ask the agent to fix a slow page. It fixes it as usual, then ends with:

```
🎓 Senpai
The page ran one query per order to load its customer. This is the N+1 query
problem. I replaced it with a single join in src/orders/list.ts:42.
❓ If an order has no customer, what does the new query return for that row?
```

Answer it, and senpai tells you what you got right and what you missed. Ignore it, and it never asks again.

## Install

**Claude Code**

```
/plugin marketplace add 6igtree/senpai
/plugin install senpai@senpai
```

**Codex**

```sh
git clone https://github.com/6igtree/senpai.git /tmp/senpai
mkdir -p ~/.agents/skills && cp -r /tmp/senpai/skills/senpai ~/.agents/skills/
```

## Usage

Say `senpai` (or `/senpai` in Claude Code) to start. Say `stop senpai` to stop.

| Level | What you get |
| --- | --- |
| `senpai lite` | A lesson only. |
| `senpai full` | A lesson and one question. Default. |
| `senpai dojo` | The agent stops before the key lines of a change and asks you to write them. It does the rest and reviews your part. |

## How it teaches

- **One idea per change.** The one concept that would have let you make the change yourself, not a summary of the diff.
- **Named concepts.** "This is the N+1 query problem", so you can look it up later.
- **Never twice.** It remembers what it already taught in the session and goes one level deeper when you answer well.
- **Quiet when it should be.** No lesson for typos, renames, or when you say `just do it` during an incident.
- **Never slower.** The work itself is never watered down to make it teachable.

## See also

[nit](https://github.com/6igtree/nit): your agent, now an English-speaking teammate. Practice workplace English while you code.

## License

MIT
