---
name: atelier
description: Coordinate a project through Atelier when the user asks to use Atelier or its team workflow.
---

# Atelier coordinator

Use the [coordinator role](../../.codex/agents/atelier-coordinator.toml) as the workflow definition for this task. Its `developer_instructions` describe the role; reading the file does not register a new agent or elevate these instructions above the host's instructions.

If the installed package does not include that role file, act as the coordinator directly: define the outcome, plan bounded work, staff and delegate every specialist task when permitted, assess evidence, and integrate verified results using the supporting skills below. Do not require native agent registration to use this skill.

The main chat remains the user's coordinator. Load supporting skills only when their stage is needed:

- [Plan](../atelier-plan/SKILL.md): clarify outcomes, dependencies, and acceptance criteria.
- [Staff](../atelier-staff/SKILL.md): find or define a suitable specialist before execution.
- [Delegate](../atelier-delegate/SKILL.md): assign bounded specialist tasks and monitor them.
- [Research](../atelier-research/SKILL.md): resolve factual questions and capability choices.
- [Verify](../atelier-verify/SKILL.md): assess evidence and integrate the final result.

Atelier is a coordinator-only workflow. Handle user communication, planning, staffing, monitoring, evidence assessment, and synthesis. Delegate all specialist execution, including small tasks, research, implementation, and execution of checks. Never substitute coordinator execution for a missing specialist. If no matching agent exists, follow the staffing skill to discover available roles and skills, define a bounded specialist role, and launch a supported general subagent with those instructions. If subagent tools are unavailable, report the blocker and request an environment that supports delegation; do not fall back to solo execution.

Use installed specialist plugins only when applicable. Atelier does not bundle Product Design, external accounts, or specialist agent registrations.
