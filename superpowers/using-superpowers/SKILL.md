---
name: using-superpowers
description: Use when starting any conversation - establishes how to find and use skills before substantial action, with Codex-appropriate guidance for checking relevant skills early
---

<SUBAGENT-STOP>
If you were dispatched as a helper agent to execute a specific task, skip this skill.
</SUBAGENT-STOP>

<EXTREMELY-IMPORTANT>
If you think there is even a 1% chance a skill might apply to what you are doing, you ABSOLUTELY MUST check the skill first.

IF A SKILL APPLIES TO YOUR TASK, YOU DO NOT HAVE A CHOICE. YOU MUST USE IT.

This is not negotiable. This is not optional. You cannot rationalize your way out of this.
</EXTREMELY-IMPORTANT>

## Instruction Priority

Superpowers skills override default system prompt behavior, but **user instructions always take precedence**:

1. **User's explicit instructions** (`AGENTS.md`, other workspace instructions, and direct requests) - highest priority
2. **Superpowers skills** - override default system behavior where they conflict
3. **Default system prompt** - lowest priority

If a workspace instruction or direct user request says "don't use TDD" and a skill says "always use TDD," follow the user's instructions. The user is in control.

## How to Access Skills

**In Codex Desktop:** Skills are discovered from the local skills filesystem. Read the relevant `SKILL.md` and follow it directly.

**In other environments:** Check your platform's documentation for how skills are loaded.

## Platform Adaptation

Some skills still use Claude Code tool names. In Codex Desktop, translate those references conservatively using `references/codex-tools.md`. If a referenced capability does not exist in the current harness, use the closest supported workflow or fall back to a manual or serial process.

# Using Skills

## The Rule

**Check relevant or requested skills BEFORE substantial action.** Even a 1% chance a skill might apply means you should inspect it before proceeding. If a checked skill turns out not to fit, you do not need to force it.

```dot
digraph skill_flow {
    "User message received" [shape=doublecircle];
    "About to plan?" [shape=doublecircle];
    "Already brainstormed?" [shape=diamond];
    "Open brainstorming skill" [shape=box];
    "Might any skill apply?" [shape=diamond];
    "Open relevant SKILL.md" [shape=box];
    "Announce: 'Using [skill] to [purpose]'" [shape=box];
    "Has checklist?" [shape=diamond];
    "Track checklist items" [shape=box];
    "Follow skill exactly" [shape=box];
    "Respond (including clarifications)" [shape=doublecircle];

    "About to plan?" -> "Already brainstormed?";
    "Already brainstormed?" -> "Open brainstorming skill" [label="no"];
    "Already brainstormed?" -> "Might any skill apply?" [label="yes"];
    "Open brainstorming skill" -> "Might any skill apply?";

    "User message received" -> "Might any skill apply?";
    "Might any skill apply?" -> "Open relevant SKILL.md" [label="yes, even 1%"];
    "Might any skill apply?" -> "Respond (including clarifications)" [label="definitely not"];
    "Open relevant SKILL.md" -> "Announce: 'Using [skill] to [purpose]'";
    "Announce: 'Using [skill] to [purpose]'" -> "Has checklist?";
    "Has checklist?" -> "Track checklist items" [label="yes"];
    "Has checklist?" -> "Follow skill exactly" [label="no"];
    "Track checklist items" -> "Follow skill exactly";
}
```

## Red Flags

These thoughts mean STOP - you're rationalizing:

| Thought | Reality |
|---------|---------|
| "This is just a simple question" | Questions are tasks. Check for skills. |
| "I need more context first" | Check for relevant skills before doing substantial exploration. |
| "Let me explore the codebase first" | Skills may tell you HOW to explore. Check first. |
| "I can check git/files quickly" | Skills may constrain how you inspect files. Check first when relevant. |
| "Let me gather information first" | Skills tell you HOW to gather information. |
| "This doesn't need a formal skill" | If a skill exists, use it. |
| "I remember this skill" | Skills evolve. Read the current version. |
| "This doesn't count as a task" | Action = task. Check for skills. |
| "The skill is overkill" | Simple things become complex. Use it. |
| "I'll just do this one thing first" | Check BEFORE doing anything substantial. |
| "This feels productive" | Undisciplined action wastes time. Skills prevent this. |
| "I know what that means" | Knowing the concept is not the same as using the skill. |

## Skill Priority

When multiple skills could apply, use this order:

1. **Process skills first** (brainstorming, debugging) - these determine HOW to approach the task
2. **Implementation skills second** - these guide execution

"Let's build X" -> brainstorming first, then implementation skills.
"Fix this bug" -> debugging first, then domain-specific skills.

## Skill Types

**Rigid** (TDD, debugging): Follow exactly. Don't adapt away discipline.

**Flexible** (patterns): Adapt principles to context.

The skill itself tells you which.

## User Instructions

Instructions say WHAT, not HOW. "Add X" or "Fix Y" doesn't mean skip workflows.
