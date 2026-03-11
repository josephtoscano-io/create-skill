# Installation

## Requirements

- [Claude Code](https://claude.ai/code) with local skills enabled

No other dependencies.

---

## Option 1 — Clone directly into Claude skills

```bash
git clone https://github.com/josephtoscano-io/create-skill ~/.claude/skills/create-skill
```

Restart your Claude Code session. The skill is available immediately.

---

## Option 2 — Manual install

1. Download or clone this repo
2. Copy the folder to `~/.claude/skills/create-skill/`
3. Confirm `SKILL.md` exists at the root of that folder
4. Restart Claude Code

---

## Invoking the skill

At any point in a session where you've built a workflow worth keeping:

```
/create-skill [skill-name]
```

The skill will ask where you want it saved:
- `~/.claude/commands/[skill-name].md` — available as `/[skill-name]` in any future session
- `~/.claude/skills/[skill-name]/SKILL.md` — installable skill format
