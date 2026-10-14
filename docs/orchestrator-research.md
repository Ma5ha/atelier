# Atelier orchestrator research

Researched 2026-10-14. These recommendations are an original synthesis, not imported third-party skills.

## Pattern

Use a manager-style coordinator that stays accountable for the user-facing answer. Specialists contribute bounded outputs; they do not take over the whole conversation. This fits the user's desire for one main contact. [Orchestration and handoffs](https://developers.openai.com/api/docs/guides/agents/orchestration).

## Needed skills

| Capability | Implementation | Why it is separate |
| --- | --- | --- |
| Planning and capability routing | `atelier-plan` | Defines success and dependencies before work starts |
| Specialist discovery and creation | `atelier-staff` | Fills missing roles using available agent tools and focused role instructions |
| Delegation and context contracts | `atelier-delegate` | Provides ownership, inputs, outputs, and coordination |
| Research and source evaluation | `atelier-research` | Separates current evidence from assumptions |
| Verification and synthesis | `atelier-verify` | Checks the integrated result before completion |
| Coordinator entry point | `atelier` | Loads relevant skills without a giant always-loaded prompt |

These five supporting skills are a design choice for Atelier, not an official required skill list. Communication, task-state tracking, conflict resolution, and failure recovery are included where they are used rather than split into more tiny skills.

Independent tasks can benefit from separate context and parallel execution. Dependent tasks and shared writes need sequencing or clear ownership. [Multi-agent guide](https://developers.openai.com/api/docs/guides/agents-api/multi-agent).

Skills provide reusable instructions and can include supporting resources; they do not themselves supply live tools. This supports a small entry skill with conditional supporting workflows. [Skill concepts](https://developers.openai.com/plugins/concepts/skills).

The coordinator-only policy is a user requirement, not an official requirement for all Codex agents. The coordinator may plan, communicate, staff, monitor, assess evidence, and synthesize outputs; specialists perform research, implementation, and check execution.

## Native agent definition

Codex documents standalone custom-agent TOML files under `.codex/agents/` for projects and `~/.codex/agents/` for personal use. Required fields are name, description, and developer instructions. Atelier includes the project definition without pinning a model. It inherits the host's capabilities and permissions. [Custom subagents](https://learn.chatgpt.com/docs/agent-configuration/subagents).

That definition describes a spawnable custom subagent. To make the main chat act as the coordinator, invoke the Atelier skill or use project instructions. Plugin installation alone is not evidence that custom-agent definitions were registered.

## Packaging and dependencies

The portable manifest and `skills/` remain the plugin components. Agent files are an accompanying project setup; copy the coordinator TOML into a destination project's `.codex/agents/` when using that role there. Follow the host's discovery and trust requirements. [Plugin packaging](https://developers.openai.com/plugins/build/plugins).

No third-party plugin contents, external credentials, model pins, or live services are bundled. Product Design can be used if separately installed. No API application is required for this Codex workflow.

## Acceptance scenarios

1. A small specialist task is delegated; the coordinator handles coordination only.
2. Independent research and implementation tasks get clear contracts and disjoint ownership.
3. A task consuming another task's output waits for that output.
4. A failed check prevents a false completion claim and triggers targeted repair.
5. Missing subagent tools result in a blocker without solo execution or fabricated agent activity.
6. Cancellation stops outstanding specialist work.
7. A missing matching role triggers discovery of available agents and skills, a bounded role definition, and launch of a supported general subagent.
8. Saving a reusable definition does not imply live registration or newly provisioned tools.

These are behavioral evaluation cases, not claims that a runtime test has passed.
