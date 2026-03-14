---
name: executing-plans
description: Use when you have a written implementation plan to execute in a separate session with review checkpoints
---

# Executing Plans

## Overview

Load the plan, review it critically, execute all tasks, and report when complete.

**Announce at start:** "I'm using the executing-plans skill to implement this plan."

**Note:** If the current harness supports helper agents, prefer `subagent-driven-development` instead of this skill. This skill exists as the serial fallback for Codex/Desktop environments where helper-agent support is unavailable or not appropriate.

## The Process

### Step 1: Load and Review Plan
1. Read the plan file
2. Review critically - identify any questions or concerns about the plan
3. If concerns exist: raise them with the user before starting
4. If no concerns exist: create a task tracker and proceed

### Step 2: Execute Tasks

For each task:
1. Mark it as `in_progress`
2. Follow each step exactly (the plan has bite-sized steps)
3. Run verifications as specified
4. Mark it as completed

### Step 3: Complete Development

After all tasks complete and are verified:
- Announce: "I'm using the finishing-a-development-branch skill to complete this work."
- **REQUIRED SUB-SKILL:** Use `finishing-a-development-branch`
- Follow that skill to verify tests, present options, and execute the user's choice

## When to Stop and Ask for Help

**STOP executing immediately when:**
- You hit a blocker (missing dependency, test fails, instruction unclear)
- The plan has critical gaps preventing starting
- You don't understand an instruction
- Verification fails repeatedly

**Ask for clarification rather than guessing.**

## When to Revisit Earlier Steps

**Return to Review (Step 1) when:**
- The user updates the plan based on your feedback
- The fundamental approach needs rethinking

**Don't force through blockers** - stop and ask.

## Remember
- Review the plan critically first
- Follow plan steps exactly
- Don't skip verifications
- Reference skills when the plan says to
- Stop when blocked, don't guess
- Never start implementation on `main`/`master` without explicit user consent

## Integration

**Required workflow skills:**
- **using-git-worktrees** - set up an isolated workspace before starting
- **writing-plans** - creates the plan this skill executes
- **finishing-a-development-branch** - completes development after all tasks
