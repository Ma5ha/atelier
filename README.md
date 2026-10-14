# Atelier

A personal Codex workshop with a coordinator and reusable supporting skills.

## Components

- `plugin.json`: portable plugin manifest.
- `.agents/plugins/marketplace.json`: marketplace catalog exposing Atelier.
- `skills/atelier/SKILL.md`: main coordinator entry point.
- `skills/atelier-plan/`: goals, dependencies, and capability selection.
- `skills/atelier-staff/`: specialist discovery and creation when a matching role is missing.
- `skills/atelier-delegate/`: specialist task contracts and coordination.
- `skills/atelier-research/`: source-based investigation and decisions.
- `skills/atelier-verify/`: acceptance checks and final integration.
- `.codex/agents/atelier-coordinator.toml`: native project custom-agent definition.
- `AGENTS.md`: instructions for working on this repository.
- `docs/orchestrator-research.md`: rationale, sources, and evaluation scenarios.

## Talk to the coordinator

In this project, ask:

> Use Atelier as my coordinator to complete this task: …

For a team workflow:

> Use Atelier and delegate independent tasks to specialists: …

The main chat coordinates the result using the Atelier skill. It handles communication,
planning, staffing, monitoring, assessment, and synthesis. Every specialist task,
including small tasks, goes to a specialist. If no suitable role exists, it discovers
available roles and skills and launches a supported general subagent with a bounded
role and task contract. Without subagent tools, it reports a blocker instead of
executing the task alone.

Reusable role definitions can be saved in the writable project when appropriate.
Creating a role does not automatically register it with the host, install skills,
or provision tools or accounts.

The TOML file also
provides a custom subagent named `atelier_coordinator` on hosts that discover it.
Ask the main agent to spawn that role if you specifically want a delegated coordinator.
It does not automatically replace the agent you talk to.

## Install and reuse

This package has not been installed through a marketplace or tested in a fresh
Codex session. Add this repository root as the marketplace source, or run from
this directory:

```sh
codex plugin marketplace add .
```

The catalog at `.agents/plugins/marketplace.json` points to the plugin at `./`.
If adding a Git URL, commit and push the catalog first so the downloaded copy
contains it. A root `plugin.json` alone is not a marketplace catalog.

Then install and enable Atelier following the [packaging guide](https://developers.openai.com/plugins/build/plugins).
After installation, select Atelier from the `$` skill suggestions.

To reuse the custom agent in another project, copy
`.codex/agents/atelier-coordinator.toml` into that project's `.codex/agents/`.
For personal discovery across projects, place it under `~/.codex/agents/` instead.
Start a fresh session and check that the host discovers the role. Agent discovery
is separate from portable plugin skill installation.

Keep the package in Git and clone it on other computers. Reconnect external
services separately. Atelier does not bundle Product Design or other plugins.
No model is pinned; host model defaults and permissions apply.

## Extend

Add focused workflows under `skills/<name>/SKILL.md`. Add specialist agent TOML
files under `.codex/agents/` when you have a concrete role. Add `mcp.json` only when
connecting a real tool server. Keep credentials out of the repository and increase
`plugin.json`'s version when distributing changes.

See [research and evaluation scenarios](docs/orchestrator-research.md) for the
coordinator's design rationale and verification boundaries.
