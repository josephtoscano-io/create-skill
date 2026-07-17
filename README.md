# create-skill

A Claude Code skill that turns any session into a reusable skill. When you've worked through a workflow with Claude — debugging a migration, generating designs, automating a task — run this skill to capture and save it as a clean, invokable command for next time.

---

## What it does

1. **Reads the current session** — understands the workflow, goal, steps, and constraints established in the conversation
2. **Distills it into a SKILL.md** — extracts only the final working approach, ignores dead ends and false starts
3. **Shows you the draft** — lets you review and adjust before saving
4. **Saves it** — writes to `~/.claude/commands/` (slash command) or `~/.claude/skills/` (installable skill), your choice

---

## Requirements

- [Claude Code](https://claude.ai/code) with local skills enabled

That's it.

---

## Installation

```bash
curl -o ~/.claude/commands/create-skill.md \
  https://raw.githubusercontent.com/josephtoscano-io/create-skill/master/create-skill.md
```

Restart your Claude Code session.

---

## Usage

At any point in a session where you've established a workflow worth keeping:

```
/create-skill [skill-name]
```

Example:

```
/create-skill acf-migrate
```

Claude will read the session, draft a SKILL.md, show it to you for review, then save it where you want it.

Works from:
- A full working session (captures the final approach)
- A partial description (Claude will ask clarifying questions before writing)

---

## License

MIT — see [LICENSE](./LICENSE)
