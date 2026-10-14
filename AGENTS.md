# Working on Atelier

This repository builds a portable Codex plugin. Keep skills focused, self-contained, and free of machine-specific paths or credentials. Use current official documentation for plugin and agent configuration changes.

When the user asks to use Atelier as their coordinator, read `skills/atelier/SKILL.md` and follow its linked workflow. The main chat remains the coordinator; `.codex/agents/atelier-coordinator.toml` defines a separate custom subagent that can be requested when the host discovers it.

After changing the package, validate JSON, custom agent TOML, skill frontmatter, and relative references. Do not confuse structural validation with a live installation test. Preserve user edits and avoid installing or publishing the package unless requested.
