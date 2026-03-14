# Superpowers Skills for Codex

![Agent](https://img.shields.io/badge/Agent-Codex-blue)
![Skills](https://img.shields.io/badge/Type-Agent%20Skills-green)
![Status](https://img.shields.io/badge/status-experimental-orange)

This repository contains a **Codex Desktop–compatible adaptation** of the `skills/` subtree from the upstream project:

[obra/superpowers](https://github.com/obra/superpowers)   v-5.0.2

The original skills were designed for **Claude Code CLI**.
This version applies **minimal compatibility adjustments** so the skills can be used in **Codex Desktop workflows**.

The goal of this project is to:

- Preserve the original methodology and workflow design
- Remove Claude-specific assumptions
- Provide a minimal, maintainable adaptation for Codex environments

---

# Installation

- **Manual**

Clone this repository and copy the  `superpowers/` folder into your local Codex skills directory.

- **Agent install**

Send the following instruction to your Codex agent:

```plaintext
Visit https://github.com/YYYYYangjijjia/superpowers-codex/install.md and follow the instructions to install the skill pack.
```

---

# Skill List

| Skill                                                                              | Description                                                                | Notes             |
| ---------------------------------------------------------------------------------- | -------------------------------------------------------------------------- | ----------------- |
| [brainstorming](superpowers/brainstorming/SKILL.md)                                   | Clarify vague ideas into concrete design directions before implementation. | Fully compatible  |
| [dispatching-parallel-agents](superpowers/dispatching-parallel-agents/SKILL.md)       | Organize independent tasks for parallel helper-agent execution.            | Conditional       |
| [executing-plans](superpowers/executing-plans/SKILL.md)                               | Execute an implementation plan step-by-step.                               | Fully compatible  |
| [finishing-a-development-branch](superpowers/finishing-a-development-branch/SKILL.md) | Finalize development work and prepare merge / PR decisions.                | Compatible        |
| [receiving-code-review](superpowers/receiving-code-review/SKILL.md)                   | Evaluate code review feedback before applying changes.                     | Fully compatible  |
| [requesting-code-review](superpowers/requesting-code-review/SKILL.md)                 | Initiate focused code reviews to discover real issues.                     | Compatible        |
| [subagent-driven-development](superpowers/subagent-driven-development/SKILL.md)       | Decompose tasks and assign them to helper agents.                          | Conditional       |
| [systematic-debugging](superpowers/systematic-debugging/SKILL.md)                     | Diagnose root causes before fixing bugs.                                   | Compatible        |
| [test-driven-development](superpowers/test-driven-development/SKILL.md)               | Write failing tests first, then implement minimal fixes.                   | Fully compatible  |
| [using-git-worktrees](superpowers/using-git-worktrees/SKILL.md)                       | Use git worktrees for isolated development environments.                   | Fully compatible  |
| [using-superpowers](superpowers/using-superpowers/SKILL.md)                           | Entry skill for the entire skill pack.                                     | Recommended entry |
| [verification-before-completion](superpowers/verification-before-completion/SKILL.md) | Verify evidence before claiming completion.                                | Compatible        |
| [writing-plans](superpowers/writing-plans/SKILL.md)                                   | Convert requirements into executable implementation plans.                 | Fully compatible  |
| [writing-skills](superpowers/writing-skills/SKILL.md)                                 | Process for creating and maintaining reusable skills.                      | Compatible        |

---

# Recommended Usage

Treat **`using-superpowers`** as the entry skill.

Instead of activating all skills at once, the expected workflow is:

1. Start with `using-superpowers`
2. Determine which skill best fits the current task
3. Switch into that skill's workflow

Typical development flow:

```

using-superpowers
→ brainstorming
→ writing-plans
→ executing-plans
→ requesting-code-review
→ verification-before-completion
→ finishing-a-development-branch

```

---

# Fully Compatible Skills

These skills have been minimally adapted to remove Claude Code dependencies and can be used directly in Codex Desktop:

- brainstorming
- writing-plans
- executing-plans
- test-driven-development
- verification-before-completion
- systematic-debugging
- requesting-code-review
- receiving-code-review
- using-git-worktrees
- finishing-a-development-branch
- writing-skills

---

# Conditionally Available Capabilities

Some workflows depend on runtime features such as **helper agents / parallel agents**.

These skills remain available but should only be used if the runtime environment supports such capabilities:

- dispatching-parallel-agents
- subagent-driven-development
- helper-agent reviewer paths

If the runtime does not support these features, these skills should degrade to sequential execution.

---

# Upstream Components Not Included

This repository only contains the `skills/` subtree from the upstream project.

The following upstream components are **not included**:

- `agents/` directory
- repository hooks
- automation integrations
- Claude Code slash commands
- Anthropic-specific runtime conventions
- repository-level configuration files

Some logic depending on specific agent APIs has been rewritten into **generalized descriptions** rather than being ported directly.

---

# Skill Directory Structure

```

superpowers-codex/
superpowers/
<skill-name>/
SKILL.md

```

Each skill includes:

```

skill-name/
SKILL.md

```

`SKILL.md` contains the required metadata fields:

```

name
description

```

These satisfy the **basic Codex skill structure requirements**.

Optional metadata files such as:

```

agents/openai.yaml
assets/
references/
scripts/

```

are not required for basic operation.

---

# Credits

Original project:

[obra/superpowers](https://github.com/obra/superpowers)

This repository is an **adaptation for Codex Desktop** and is not affiliated with the original authors.

---
