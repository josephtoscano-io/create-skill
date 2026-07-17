# Installation

## Requirements

- [Claude Code](https://claude.ai/code) with local skills enabled

No other dependencies.

---

## Option 1 — curl the command file

```bash
curl -o ~/.claude/commands/create-skill.md \
  https://raw.githubusercontent.com/josephtoscano-io/create-skill/master/create-skill.md
```

On Windows the target is `C:\Users\<you>\.claude\commands\create-skill.md`. Reload Claude Code and run `/create-skill`.

---

## Option 2 — Manual install

1. Download or clone this repo
2. Copy `create-skill.md` into `~/.claude/commands/`
   (Windows: `C:\Users\<you>\.claude\commands\`)
3. Reload Claude Code

Only that one file is needed — the rest of the repo is documentation.

---

## Invoking the skill

At any point in a session where you've built a workflow worth keeping:

```
/create-skill [skill-name]
```

The skill saves to `~/.claude/commands/[skill-name].md` and is immediately available as `/[skill-name]` in any future session.
