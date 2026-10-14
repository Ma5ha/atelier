---
name: atelier-staff
description: Find or define a specialist for an Atelier task when no suitable agent is available, then launch it through supported subagent tools.
---

# Staff the task

Every execution task has a specialist owner, including small edits, research, implementation, artifact production, and running verification. The coordinator owns planning, communication, staffing, monitoring, assessment, and synthesis.

Inspect the host's available agent types, installed skills, and relevant project role definitions. Reuse a suitable specialist before creating a new role. Assess suitability by required expertise, available tools, and scope; a name alone is not evidence of capability.

When no matching specialist exists, define one with a concrete name, purpose, expertise, relevant skills, necessary tools, scope, expected output, and acceptance criteria. Use the task contract in [Delegate](../atelier-delegate/SKILL.md). A supported general-purpose subagent with these instructions is a valid task-specific specialist; do not pass an invented role name as an unregistered native agent type.

Launch through the host's supported subagent tools, passing the role definition and bounded task. Keep host defaults unless the user chooses otherwise. Confirm the spawn succeeded before reporting the specialist as active. Missing expertise instructions can be supplied; missing permissions, credentials, or tools cannot be created by a prompt. Assign capability research to an available research specialist if needed, and request the specific missing setup only when it blocks execution.

For a role likely to recur, save a reusable definition in the writable target project when appropriate. On Codex hosts supporting standalone agent TOML, use `.codex/agents/<role-name>.toml` with `name`, `description`, and `developer_instructions`. Preserve existing files, avoid machine-specific paths, and use the current documented host format. If role persistence needs protected writes, follow the host's approval mechanism; the immediate specialist can still run using explicit role instructions when permitted.

Saving a file does not prove the running host registered it. Until discovery is confirmed, continue using an available agent type with the role instructions. Do not modify installed plugin caches or global configuration to persist a role. Add reusable skills to Atelier's source only when the user requests package development; otherwise keep task-specific roles in the target project.

If no subagent execution is available, state that specialist execution is blocked and identify what must be enabled. The coordinator may prepare a brief and staffing plan but must not perform the specialist task itself. Do not fabricate an agent, silently switch to solo execution, or mark a role definition as a completed deliverable for the original task.
