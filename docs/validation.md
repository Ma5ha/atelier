# Validation

Checked on 2026-10-14:

- Parsed `plugin.json` as JSON and checked the package name.
- Parsed the custom-agent file with Python's TOML parser and checked its required string fields.
- Checked the skills for complete name/description frontmatter and valid names.
- Resolved every local Markdown link from the skills to an existing file.
- Confirmed the agent definition leaves model selection to the host.

The bundled skill validator could not run because PyYAML is unavailable in the
Python runtimes checked. The structural checks above used Python's standard library.
They do not validate the manifest against its remote JSON schema.

Marketplace installation, fresh-session agent discovery, and live delegated
execution have not been tested. See `orchestrator-research.md` for acceptance scenarios.

Earlier instruction review covered the previous policy. The coordinator-only update adds
mandatory specialist execution, missing-role staffing, and a blocker when subagent
tools are unavailable. Those updated scenarios still require behavioral testing;
structural validation does not demonstrate live delegation or agent discovery.
