---
name: atelier-delegate
description: Assign, monitor, and integrate bounded specialist tasks in an Atelier workflow when delegation is authorized and subagent tools are available.
---

# Delegate work

Confirm the environment supports subagents and that delegation is authorized. A requested Atelier team workflow permits delegation within its stated scope, subject to the host's instructions. Delegate every specialist execution task, including tiny tasks. If subagent tools are unavailable, disclose the blocker and stop dependent execution; there is no solo execution fallback.

Use a registered specialist when it matches the task. Otherwise follow [Staff](../atelier-staff/SKILL.md): discover available roles and skills, define a bounded role, and give a supported general subagent explicit role instructions. Do not invent agent types or claim a role document is registered. Preserve the user's model choice; otherwise inherit defaults.

Give each specialist this compact task contract:

- Objective and expected artifact or answer.
- Relevant context, decisions, inputs, and available skills.
- Scope and explicit file/module ownership for edits.
- Dependencies and work that must wait.
- Acceptance criteria and appropriate verification.
- Constraints and existing authorization boundaries.
- Return format: result, evidence, files changed, checks run, unresolved issues.

Tell editing specialists they share the workspace, must preserve others' work, and must coordinate overlapping edits. Use disjoint ownership or isolated worktrees when the host permits; do not run simultaneous writes to the same file or external resource. Pass only relevant context, never unnecessary credentials.

Stay responsible for the user-facing result. Continue independent coordination while specialists run; do not execute specialist work yourself. Respect concurrency limits, wait with the host's coordination tools, and avoid repeated unchanged polling. Reuse a specialist for related follow-ups. Do not create separate user-owned chats merely to implement a subtask.

Treat specialist output as evidence to assess. Assign specialists to resolve inconsistent findings using primary sources, reproduction, or a targeted check, then assess their evidence. Reassign or narrow failed tasks; after the same failure repeats without new evidence, change approach or report the specific blocker. Do not expand scope or permissions to force completion.

On cancellation or a superseding goal, stop outstanding delegated work. Before finishing, account for every task and integrate all required outputs.
