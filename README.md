# Office Wizards Agent Skills

Agent Skills for Office Wizards, packaged for the open Agent Skills ecosystem and installable with Vercel's `skills` CLI or as a Claude Code, Codex, or Cursor plugin.

This repo is the host-facing skills and plugin distribution layer. Product implementations are delivered separately through product CLIs such as `workbook-wizard`.

## Install in Cursor

In Cursor, install the plugin from the Cursor marketplace when available, or run the following from inside a Cursor session:

```text
/add-plugin office-wizards
```

## Install in Claude Code

In Claude Code, add this repo as a marketplace and install the plugin:

```text
/plugin marketplace add officewizards/officewizards-agent-skills
/plugin install office-wizards@office-wizards
```

## Install in Codex

In Codex (CLI, app, or VS Code extension), add this repo as a marketplace and install the plugin:

```text
codex plugin marketplace add officewizards/officewizards-agent-skills
codex plugin add office-wizards@office-wizards
```

## Install via the Agent Skills CLI

```bash
npx skills add https://github.com/officewizards/officewizards-agent-skills
```

List available skills without installing:

```bash
npx skills add https://github.com/officewizards/officewizards-agent-skills --list
```

## Available Skills

### `officewizards`

Route Microsoft Office desktop automation requests to the right Office Wizards product skill.

### `workbook-wizard`

Inspect and automate Microsoft Excel desktop for Windows with the `workbook-wizard` CLI.

Use this when a user mentions Workbook Wizard, Microsoft Excel desktop, open workbooks, active selections, ranges, formulas, charts, PivotTables, macros, or local Windows Excel automation.

This public repository is the canonical agent-facing source of truth. The Excel CLI package supplies the local Windows implementation behind:

```bash
npx -y workbook-wizard <command> -o json
```

## Planned Product Skills

- `doc-wizard`
- `deck-wizard`
- `inbox-wizard`

These will be added as sibling skills when the corresponding product CLIs exist.
