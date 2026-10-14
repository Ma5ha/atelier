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
provides a custom subagent named `atelier` on hosts that discover it.
Ask the main agent to spawn that role if you specifically want a delegated coordinator.
It does not automatically replace the agent you talk to.

## Install and reuse

Package validation does not test marketplace installation or fresh-session
behavior. Add this repository root as the marketplace source, or run from this
directory:

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

## Branding and updates

The plugin's listing logo and composer icon are declared in
`plugin.json` under `extensions.com.openai.interface`. Their paths are relative
to the plugin root; keep the referenced files in `assets/` when distributing.
The square [icon](assets/atelier-icon.png) serves both plugin surfaces, while the
transparent [wordmark](assets/atelier-wordmark.png) is available for light backgrounds.
See the [official icon requirements](https://developers.openai.com/plugins/deploy/submission#icons-and-screenshots).

For a Git-backed marketplace, commit and push the new package before refreshing
the source. For a local marketplace, update the source directory first. Refresh
the configured Atelier marketplace with:

```sh
codex plugin marketplace upgrade atelier-marketplace
```

Then restart the desktop app and check Atelier in the Plugins Directory and a
fresh chat. Installed plugins load from a cached copy, so editing this repository
alone is not proof that the installed plugin changed. These steps follow the
[official marketplace guide](https://developers.openai.com/plugins/build/plugins#add-a-marketplace-from-the-cli).

Update buttons and badges belong to the host app. The documented manifest fields
do not offer a switch to create one. Increasing the package version identifies a
release; it does not guarantee a visible update badge. This package's branding
and refresh behavior still need a live installation check.

## Extend

Add focused workflows under `skills/<name>/SKILL.md`. Add specialist agent TOML
files under `.codex/agents/` when you have a concrete role. Add `mcp.json` only when
connecting a real tool server. Keep credentials out of the repository and increase
`plugin.json`'s version when distributing changes.

See [research and evaluation scenarios](docs/orchestrator-research.md) for the
coordinator's design rationale and verification boundaries.
