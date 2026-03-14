# Codex Tool Mapping

Skills in this package were originally written with Claude Code terminology. In this Codex Desktop environment, use the closest supported equivalent and do not invent missing capabilities.

| Skill references | Codex Desktop equivalent |
|------------------|--------------------------|
| `Skill` tool | Open the relevant `SKILL.md` from the skills filesystem and follow it |
| `TodoWrite` | Use the task tracker / plan mechanism available in the current harness |
| `Read`, `Write`, `Edit` | Use the native filesystem tools in the current harness |
| `Bash` | Use the native shell tool |
| `Task` tool / subagent dispatch | Only use if the current Codex harness actually exposes helper-agent support |
| Multiple `Task` calls in parallel | Only use if helper-agent support exists; otherwise decompose the work and run it serially |

## Important Limitation

Do **not** assume Codex Desktop has built-in helper-agent dispatch just because a skill mentions it.

If the current harness does not expose helper agents:
- use the serial fallback described in the skill
- or adapt the workflow to a single-session process

If the current harness does expose helper agents:
- keep prompts tightly scoped
- provide task-local context instead of full session history
- review returned work before proceeding
