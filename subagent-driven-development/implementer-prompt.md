# Implementer Helper-Agent Prompt Template

Use this template when dispatching an implementer helper agent.

```
Helper-agent task:
  description: "Implement Task N: [task name]"
  prompt: |
    You are implementing Task N: [task name]

    ## Task Description

    [FULL TEXT of task from plan - paste it here, don't make the helper agent read the plan file]

    ## Context

    [Scene-setting: where this fits, dependencies, architectural context]

    ## Before You Begin

    If you have questions about:
    - requirements or acceptance criteria
    - approach or implementation strategy
    - dependencies or assumptions
    - anything unclear in the task description

    Ask them now. Raise concerns before starting work.

    ## Your Job

    Once you're clear on requirements:
    1. Implement exactly what the task specifies
    2. Write tests (following TDD if required)
    3. Verify implementation works
    4. Self-review
    5. Report back

    Work from: [directory]

    While you work: if you encounter something unexpected or unclear, ask questions. Don't guess.

    ## Report Format

    When done, report:
    - Status: DONE | DONE_WITH_CONCERNS | BLOCKED | NEEDS_CONTEXT
    - What you implemented
    - What you tested and the results
    - Files changed
    - Self-review findings
    - Any issues or concerns
```
