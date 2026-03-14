# Testing Skills With Helper Agents

**Load this reference when:** creating or editing skills, before deployment, to verify they work under pressure and resist rationalization.

## Overview

Testing skills is TDD applied to process documentation.

You run scenarios without the skill (RED), write the skill to address observed failures (GREEN), then close loopholes and re-test (REFACTOR).

**Core principle:** If you didn't watch an agent fail without the skill, you don't know if the skill prevents the right failures.

## When to Use

Test skills that:
- enforce discipline
- have compliance costs
- could be rationalized away
- contradict immediate goals such as speed over quality

Don't spend this much effort on pure reference files unless they are high-stakes.

## RED Phase: Baseline Testing

Run the scenario WITHOUT the skill and document:
- what the agent chose
- what rationalizations it used
- what pressures triggered the bad choice

Good pressure scenarios combine 3+ factors:
- time pressure
- sunk cost
- authority pressure
- exhaustion
- pragmatic shortcut framing

## GREEN Phase: Minimal Skill

Write only enough to counter the failures you actually observed.

Then re-run the same scenario WITH the skill and verify the behavior changes.

## REFACTOR Phase: Close Loopholes

When the agent still finds a workaround:
- capture the exact new rationalization
- add an explicit counter
- add it to the rationalization table or red-flags section
- re-test

Repeat until the behavior is stable.

## If Helper Agents Are Not Available

Use the same methodology with a fresh session or tightly controlled prompts:
- keep scenarios concrete
- force an explicit choice
- record the exact wording of failures
- revise the skill
- re-run

The method matters more than the exact harness.

## Good Scenario Properties

1. Concrete options
2. Real constraints
3. Realistic stakes
4. No easy escape hatch
5. Clear pass/fail outcome

## Quick Checklist

- [ ] Baseline run without the skill
- [ ] Failures documented verbatim
- [ ] Minimal skill written
- [ ] Re-test with the skill
- [ ] Loopholes patched
- [ ] Final re-test passed

## Historical Example

`examples/CLAUDE_MD_TESTING.md` is kept as an upstream historical example. It demonstrates the methodology, but its file names and environment assumptions are Claude-specific.
