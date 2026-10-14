# Validation

Checked on 2026-10-14:

- Bumped the package to `0.3.2` and checked the OpenAI interface fields against
  the [official packaging guide](https://developers.openai.com/plugins/build/plugins).
- Resolved `composerIcon` and `logo` to the square PNG in `assets/`; checked its
  PNG header, 1254 by 1254 dimensions, and size below the documented 5 MiB limit.
- Checked README links to both branding assets and ran `git diff --check`.
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
The new branding has not been checked in the installed Plugins Directory or
composer. Marketplace refresh and any host update button or badge have not been
tested; the package declares no unsupported update UI field.

Earlier instruction review covered the previous policy. The coordinator-only update adds
mandatory specialist execution, missing-role staffing, and a blocker when subagent
tools are unavailable. Those updated scenarios still require behavioral testing;
structural validation does not demonstrate live delegation or agent discovery.

The product-designer role was added using the documented standalone TOML format.
Its design instructions and tool routes have been reviewed, but no design task,
native runtime check, Figma access test, or fresh-session discovery test has run.
Assess design quality on the first project trial described in `product-designer.md`.
