# senpai 🎓

**English** | [日本語](./README.ja.md)

**Your agent writes the code. You still learn.**

AI agents write more of our code every day, and many of us feel it: we ship faster, but we understand less. senpai is a skill for Claude Code and Codex that turns your agent into the senior engineer next to you. It still does the work at full speed. But for each change, it hands you the one piece that sits right at the edge of your level.

## What it looks like

You are aiming for mid-level. You ask the agent to speed up a slow page. It writes the change, but leaves one small hole for you:

```python
def list_orders(db):
    orders = db.query("SELECT * FROM orders")
    # TODO(senpai): implement this — mid-level must-know
    # Load the customers for all orders in one query, not one per order.
    # Hint: look up "N+1 query problem".
    raise NotImplementedError
```

```
🎓 Senpai [mid-level must-know]
Loading one customer per order runs 101 queries for 100 orders.
Fill in src/orders.py:4 and I'll review it.
```

Fill it in, and senpai reviews it. Say `you do it`, and it fills the hole itself and moves on.

## The ladder

senpai tags every idea in a change by the career level that must know it:

| Level | Must know, for example |
| --- | --- |
| junior | Off-by-one, null and empty input, reading an error message |
| mid | N+1 queries, indexes, caching, what to mock in tests |
| senior | Race conditions, idempotency, retries and timeouts, safe migrations |
| staff | API compatibility, consistency vs availability, cost of ownership |

Then it treats each idea by where it sits relative to you:

| The idea is | senpai |
| --- | --- |
| Below your level | Just writes it. You already know it. |
| At your level | Leaves a 1-5 line hole for you to implement. |
| Above your level | Writes it, then teaches it in three sentences. |

When your holes come back clean a few times in a row, senpai suggests moving up. It never switches on its own. Your level is saved in `~/.senpai/level`.

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

Say `senpai` (or `/senpai` in Claude Code) to start. The first time, it asks which level you are aiming for. Switch any time with `senpai junior`, `senpai mid`, `senpai senior`, or `senpai staff`. Say `stop senpai` to stop.

## What it never does

- **Never a hole where it hurts.** Auth, payments, deletion, and destructive migrations are always written by the agent, and taught as a lesson instead.
- **Never more than one hole** per response, so the work keeps moving.
- **Never during an incident.** Say `just do it` and it stays quiet until the next calm task.
- **Never slower.** The work itself is never watered down to make it teachable.

## See also

[nit](https://github.com/6igtree/nit): your agent, now an English-speaking teammate. Practice workplace English while you code.

## License

MIT
