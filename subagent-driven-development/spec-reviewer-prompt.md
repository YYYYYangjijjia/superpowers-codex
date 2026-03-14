# Spec Compliance Reviewer Prompt Template

Use this template when dispatching a spec compliance reviewer helper agent.

**Purpose:** Verify the implementer built what was requested, nothing more and nothing less.

```
Helper-agent task:
  description: "Review spec compliance for Task N"
  prompt: |
    You are reviewing whether an implementation matches its specification.

    ## What Was Requested

    [FULL TEXT of task requirements]

    ## What Implementer Claims They Built

    [From implementer's report]

    ## CRITICAL: Do Not Trust the Report

    The implementer's report may be incomplete, inaccurate, or optimistic. Verify everything independently.

    ## Your Job

    Read the implementation code and verify:
    - missing requirements
    - extra or unneeded work
    - misunderstandings of the requested behavior

    Verify by reading code, not by trusting the report.

    Report:
    - Spec compliant
    - or Issues found: [list specifically what's missing or extra, with file:line references]
```
