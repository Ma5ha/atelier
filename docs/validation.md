# Validation

Checked on 2026-10-14:

- Parsed `plugin.json` as JSON and checked the package name.
- Parsed `.agents/plugins/marketplace.json` and resolved its plugin source to
  the repository root containing `plugin.json`.
- Parsed both custom-agent files with Python's TOML parser and checked their required string fields.
- Checked the skills for complete name/description frontmatter and valid names.
- Resolved every local Markdown link from the skills to an existing file.
- Confirmed both agent definitions leave model selection to the host.
- Checked the product-designer role brief's local Markdown reference.

The bundled skill validator could not run because PyYAML is unavailable in the
Python runtimes checked. The structural checks above used Python's standard library.
They do not validate the manifest against its remote JSON schema.

Marketplace installation, fresh-session agent discovery, and live delegated
execution have not been tested. See `orchestrator-research.md` for acceptance scenarios.

Earlier instruction review covered the previous policy. The coordinator-only update adds
mandatory specialist execution, missing-role staffing, and a blocker when subagent
tools are unavailable. Those updated scenarios still require behavioral testing;
structural validation does not demonstrate live delegation or agent discovery.

The product-designer role was added using the documented standalone TOML format.
Its design instructions and tool routes have been reviewed, but no design task,
native runtime check, Figma access test, or fresh-session discovery test has run.
Assess design quality on the first project trial described in `product-designer.md`.
