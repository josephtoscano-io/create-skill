# Create Skill

Distill the current session into a reusable Claude Code skill and save it as a command.

## Arguments
$ARGUMENTS

Expected format: `[skill-name]`

Example: `acf-migrate`

---

## Steps

### 1. Parse arguments
Extract `skillName` — kebab-case name for the new skill.

### 2. Ask for save location
Ask the user where to save the skill:
- `~/.claude/commands/[skillName].md` — saves as a slash command, invoked with `/[skillName]`
- `~/.claude/skills/[skillName]/SKILL.md` — saves as an installable skill

Default to `~/.claude/commands/` if they're unsure.

### 3. Understand the workflow
Read the current conversation and identify:
- **Goal** — what does this skill accomplish?
- **Trigger** — when would someone invoke it?
- **Inputs** — what arguments or context does it need?
- **Steps** — what is the sequence of actions?
- **Rules/constraints** — what must always be true? What should never happen?
- **Outputs** — what does it produce?

If the session is exploratory or contains false starts, extract only the final, working approach. Ignore dead ends.

If the conversation is thin (e.g. the user is describing a skill from scratch rather than demonstrating one), ask clarifying questions before writing — don't guess at missing steps.

### 4. Draft the SKILL.md
Write a SKILL.md with this structure:

```
# [Skill Title]

[1–2 sentence description of what it does and when to use it.]

## Arguments
$ARGUMENTS

Expected format: `[...]`
Example: `[...]`

(Omit this section entirely if the skill takes no arguments.)

---

## Steps

### 1. [Step name]
[Clear, actionable instructions.]

### 2. [Step name]
...

---

## Rules
- [Constraint that must always be followed]
- [What never to do]

(Omit if no strong constraints exist.)
```

Rules for writing good SKILL.md content:
- Use imperative voice: "Read the file", not "You should read the file"
- Be specific — reference actual file paths, CLI commands, patterns where relevant
- Include code examples for any non-obvious syntax
- No fluff, no preamble, no "here's what I'll do" narration
- Steps should be granular enough that nothing is left to interpretation

### 5. Show and confirm
Display the full draft SKILL.md to the user. Ask:
"Does this look right, or should I adjust anything before saving?"

Wait for confirmation. Apply any requested changes before proceeding.

### 6. Save
Write the confirmed SKILL.md to the path chosen in step 2.

If a file already exists at that path, warn the user and ask before overwriting.

### 7. Report back
Confirm the file was saved and remind the user how to invoke it:
- If saved to `commands/`: `/[skillName]`
- If saved to `skills/`: reference the skill name in your prompt
