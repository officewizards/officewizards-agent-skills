---
name: workbook-wizard
description: Control Microsoft Excel desktop for Windows through the Workbook Wizard npx CLI. Use when an agent needs to inspect Excel installation state, authenticate the local CLI, list workbooks, inspect the current selection, or automate Excel desktop without browser automation, localhost servers, Office.js add-ins, or raw PowerShell-first workflows.
allowed-tools: Bash(npx -y workbook-wizard *)
user-invocable: true
---

# Workbook Wizard

Workbook Wizard is a Windows-only CLI for Microsoft Excel desktop automation. Always run commands as:

```bash
npx -y workbook-wizard <command> -o json
```

Use JSON output for data-returning commands and `-y` when a command supports non-interactive confirmation.

## First Step

Run:

```bash
npx -y workbook-wizard info -o json
```

For command discovery, run:

```bash
npx -y workbook-wizard help -o json
npx -y workbook-wizard help read-range -o json
```

If the user is not authenticated, run:

```bash
npx -y workbook-wizard login
npx -y workbook-wizard whoami -o json
```

Authentication is local in the initial desktop-only version. Future hosted features can replace the same command shape with a browser login flow.

## Common Commands

Check Excel desktop and COM:

```bash
npx -y workbook-wizard check-install -o json
```

List open workbooks:

```bash
npx -y workbook-wizard workbooks -o json
```

Inspect the active Excel selection:

```bash
npx -y workbook-wizard current-selection -o json
```

## Workflow

1. Run `info`.
2. Run `check-install` before assuming desktop Excel is available.
3. Run `workbooks` and `current-selection` to identify the active context.
4. Prefer wrapped CLI commands for routine operations.
5. Serialize Excel operations. Desktop COM calls into the same Excel instance can reject concurrent automation.
6. Verify writes by reading the touched ranges and saving or exporting artifacts when relevant.

## References

Read `references/cli-reference.md` when choosing commands or when updating this skill as new CLI commands ship.

## Release Notes

- Target Microsoft Excel desktop on Windows only.
- The public skills repository intentionally does not contain the private CLI implementation.
- Agents should treat `npx -y workbook-wizard` as the executable boundary.
- A different strategy will be needed for Excel web, macOS Excel, or non-desktop Office integrations.
