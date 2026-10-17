# Plugin System Proposal

**Status:** Concept only. The plugin API has not been implemented.

## Goals

- Keep the core application independent of optional features.
- Allow community developers to add commands, panels, workflows, import/export helpers, and integrations.
- Support AI as an optional plugin category.
- Provide version compatibility and clear failure behavior.
- Reduce accidental access to user files and other sensitive resources.

## Initial plugin categories

- CAD tools and feature generators.
- Import/export and file-format helpers.
- Manufacturing and 3D-printing workflows.
- Simulation and analysis integrations.
- AI provider adapters and AI-assisted modeling.
- User interface panels and workflow automation.

## Proposed first API

The first API should stay intentionally small:

- **Plugin manifest:** identifier, version, compatible application/API versions, entry point, permissions, and license metadata.
- **Command API:** register documented commands and validate inputs.
- **Document API:** read document context and apply edits through transactions.
- **UI API:** register panels, menus, toolbars, and commands.
- **Provider API:** optional interface for local or remote AI inference.
- **GPU services:** documented acceleration interfaces where useful, without requiring every plugin to use the same backend.

## Security principles

- Treat third-party plugins as untrusted by default.
- Make permissions visible and explicit.
- Avoid unrestricted in-process execution where practical.
- Consider subprocess isolation for Python plugins.
- Do not expose credentials or arbitrary filesystem/network access by default.
- Validate plugin-provided parameters before modifying a document.
- Keep an audit trail for document-changing commands where practical.
- Provide disable/uninstall and recovery paths for broken plugins.

A plugin manager is not itself a sandbox. Security claims must be supported by the actual isolation design and tests.

## Distribution

A future registry should include package versions, source links, licenses, compatibility metadata, dependency declarations, signatures or provenance, and a reporting process. A community registry is a later milestone, not a prerequisite for the first plugin API.
