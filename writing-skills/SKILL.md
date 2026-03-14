---
name: writing-skills
description: Use when creating new skills, editing existing skills, or verifying skills work before deployment
---

# Writing Skills

## Overview

Writing skills is Test-Driven Development applied to process documentation.

You create pressure scenarios, watch an agent or workflow fail without the skill, write the skill, verify that the skill changes behavior, and then close loopholes.

**Core principle:** If you didn't watch an agent fail without the skill, you don't know whether the skill teaches the right thing.

**Required background:** You MUST understand `test-driven-development` before using this skill.

## What is a Skill?

A **skill** is a reference guide for proven techniques, patterns, or tools. Skills help future agents find and apply effective approaches.

**Skills are:** reusable techniques, patterns, tools, and reference guides.

**Skills are NOT:** narratives about how you solved one specific problem once.

## When to Create a Skill

**Create when:**
- The technique was not intuitively obvious
- You would reference it again across projects
- The pattern applies broadly
- Other agents or future sessions would benefit

**Don't create for:**
- One-off solutions
- Standard practices already well documented elsewhere
- Project-specific conventions better placed in workspace instructions
- Mechanical constraints that should be enforced with automation instead

## TDD Mapping for Skills

| TDD Concept | Skill Creation |
|-------------|----------------|
| Test case | Pressure scenario with an agent or realistic workflow |
| Production code | Skill document (`SKILL.md`) |
| Test fails (RED) | Agent violates the rule without the skill |
| Test passes (GREEN) | Agent complies with the skill present |
| Refactor | Close loopholes while keeping compliance |

The whole process follows RED-GREEN-REFACTOR.

## Directory Structure

```text
skills/
  skill-name/
    SKILL.md
    supporting-file.*
```

Use extra files only when they materially improve clarity:
- heavy reference material
- reusable scripts/tools
- templates or examples that are better kept separate

## SKILL.md Structure

**Frontmatter:**
- `name`
- `description`

**Description rules:**
- Start with `Use when...`
- Describe triggering conditions, not the whole workflow
- Use third person / neutral wording
- Include concrete symptoms and contexts

**Recommended structure:**

```markdown
---
name: skill-name
description: Use when [specific triggering conditions and symptoms]
---

# Skill Name

## Overview

## When to Use

## Core Pattern

## Quick Reference

## Common Mistakes
```

## Discovery Optimization

Descriptions are for discovery. They should answer: "Should this skill be loaded right now?"

**Good:**
```yaml
description: Use when executing implementation plans with independent tasks in the current session
```

**Bad:**
```yaml
description: Use when executing plans - dispatches a reviewer between tasks and finishes with branch cleanup
```

Why bad: a workflow summary can become a shortcut that causes the agent to skip the actual skill body.

## Writing Rules

- Be concise
- Use active names
- Prefer one excellent example over many mediocre ones
- Reference related skills by name or relative path
- Keep file references shallow and obvious
- Avoid narrative storytelling
- Avoid over-explaining concepts the model already knows

## Testing Skills

Before deploying a skill, test it against realistic scenarios.

For discipline-enforcing skills:
- run a baseline scenario without the skill
- document the exact rationalizations and failures
- write the minimum skill that prevents those failures
- retest under pressure
- add explicit counters for new loopholes

For reference or technique skills:
- test whether the agent can find and apply the right information
- test common edge cases
- verify that gaps are obvious

If helper agents are available, use them for independent validation. If not, simulate the same pressure scenarios manually in a fresh session or with tightly controlled prompts.

For the detailed methodology, see `testing-skills-with-subagents.md`.

## Supporting References

- `anthropic-best-practices.md` is a historical reference from the original upstream package. Treat it as optional background, not as Codex-specific guidance.
- `examples/CLAUDE_MD_TESTING.md` is a historical example of a Claude-oriented test campaign. Use it only as an example of testing methodology, not as deployment guidance for Codex Desktop.

## Common Mistakes

| Mistake | Fix |
|---------|-----|
| Writing the skill before testing | Run a baseline scenario first |
| Description summarizes the workflow | Keep description to triggering conditions |
| Too much prose | Cut anything the model likely already knows |
| Too many supporting files | Keep the skill discoverable and shallow |
| Untested deployment | Validate before shipping |

## Skill Creation Checklist

- [ ] Run a baseline scenario without the skill
- [ ] Document exact failures or rationalizations
- [ ] Write the minimal skill that addresses those failures
- [ ] Re-test with the skill present
- [ ] Add counters for any new loopholes
- [ ] Check name and description quality
- [ ] Confirm references and examples are still accurate

## The Bottom Line

Creating skills is TDD for process documentation.

Same rule as code: no skill should be treated as complete until it has been validated against realistic use.
