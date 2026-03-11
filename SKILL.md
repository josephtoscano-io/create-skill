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

### 2. Understand the workflow
Read the current conversation and identify:
- **Goal** — what does this skill accomplish?
- **Trigger** — when would someone invoke it?
- **Inputs** — what arguments or context does it need?
- **Steps** — what is the sequence of actions?
- **Rules/constraints** — what must always be true? What should never happen?
- **Outputs** — what does it produce?

If the session is exploratory or contains false starts, extract only the final, working approach. Ignore dead ends.

If the conversation is thin (e.g. the user is describing a skill from scratch rather than demonstrating one), ask clarifying questions before writing — don't guess at missing steps.

### 3. Draft the SKILL.md
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

### 4. Show and confirm
Display the full draft SKILL.md to the user. Ask:
"Does this look right, or should I adjust anything before saving?"

Wait for confirmation. Apply any requested changes before proceeding.

### 5. Save
Write the confirmed SKILL.md to:
`~/.claude/commands/[skillName].md`

If a file already exists at that path, warn the user and ask before overwriting.

### 6. Report back
Confirm the file was saved and remind the user how to invoke it:
`/[skillName]`
