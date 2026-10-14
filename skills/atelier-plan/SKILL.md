---
name: atelier-plan
description: Define outcomes, task boundaries, dependencies, and acceptance criteria for an Atelier project before implementation or delegation.
---

# Plan work

Extract the requested deliverable, intended user, constraints, and observable acceptance criteria. Preserve explicit choices; separate assumptions from requirements. Ask only for missing decisions that would change the result.

Inspect relevant project context before selecting an approach. Map the work into bounded tasks with inputs, outputs, dependencies, and ownership. Parallelize independent work only; sequence work that consumes another task's output. Assign every specialist task to a specialist, including small tasks. The coordinator owns planning and coordination only.

Choose specialists by the question they must answer, not by an arbitrary team size. Discover available skills, registered agent types, and tools before promising capabilities. Prefer existing focused skills over inventing replacements. Follow [Staff](../atelier-staff/SKILL.md) to fill a missing role using a supported general subagent with explicit instructions. Do not take over specialist execution when a capability is missing.

For substantial work, keep a compact task ledger in the host's planning tool. If no planning tool exists and resumable tracking matters, use a task-specific file under `.atelier/tasks/` in the target project. Record goal, decisions, task owner, dependencies, status, artifact locations, acceptance criteria, and unresolved blockers. Do not store secrets or hidden reasoning. For short work, conversation context is enough.

Revise the plan when evidence changes it. Stop adding work when the user's acceptance criteria are satisfied.
