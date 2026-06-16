<!-- Generated from workbook-wizard/skills-src/workbook-wizard/SKILL.md.tmpl. Do not edit directly. -->
---
name: workbook-wizard
description: Control Microsoft Excel desktop for Windows through the Workbook Wizard npx CLI. Use when an agent needs to inspect Excel, list/open/create/save workbooks, read or write sheets and ranges, calculate, import/export, manage names/tables/charts, format/sort/filter/find/replace, run macros or temporary VBA, inspect the current selection, or automate Excel without browser automation, localhost servers, Office.js add-ins, or raw PowerShell-first workflows.
allowed-tools: Bash(npx -y workbook-wizard *)
user-invocable: true
---

# Workbook Wizard

Workbook Wizard is a Windows-only CLI for Microsoft Excel desktop automation.

This rendered public skill resolves Workbook Wizard from npm latest with 
px -y workbook-wizard.

Run commands as:

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

Authentication is local in the desktop-only version.

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

Read and write a range:

```bash
npx -y workbook-wizard read-range --workbook-path ".\book.xlsx" --worksheet "Sheet1" --range "A1:D20" --include-formulas --include-text -o json
npx -y workbook-wizard write-range --workbook-path ".\book.xlsx" --worksheet "Sheet1" --range "A1" --value-json '[[ "Name", "Amount" ], [ "A", 10 ]]' -o json
```

On Windows shells that strip nested JSON quotes, write the payload to a file and use:

```bash
npx -y workbook-wizard write-range --workbook-path ".\book.xlsx" --worksheet "Sheet1" --range "A1" --value-json-file ".\values.json" -o json
```

Create a table and chart:

```bash
npx -y workbook-wizard create-table --worksheet "Data" --range "A1:D20" --table-name "AgentTable" --has-headers -o json
npx -y workbook-wizard create-chart --worksheet "Data" --range "A1:D20" --chart-name "AgentChart" --chart-type column --title "Agent Chart" -o json
```

Run temporary VBA:

```bash
npx -y workbook-wizard run-vba --workbook-path ".\book.xlsm" --vba-code "Public Function Main() As String`nMain = ActiveWorkbook.Name`nEnd Function" -o json
```

## Operation Set

`check-install`, `workbooks`, `sheets`, `new-workbook`, `open-workbook`, `close-workbook`, `save`, `save-as`, `used-range`, `read-range`, `write-range`, `clear-range`, `set-formula`, `calculate`, `export-pdf`, `import-csv`, `add-sheet`, `rename-sheet`, `delete-sheet`, `copy-sheet`, `list-names`, `set-name`, `delete-name`, `list-tables`, `create-table`, `resize-table`, `delete-table`, `list-charts`, `create-chart`, `delete-chart`, `format-range`, `sort-range`, `autofilter`, `find`, `replace`, `protect-sheet`, `unprotect-sheet`, `workbook-info`, `run-macro`, `run-vba`, `run-script`, `current-selection`, `control-workbook`, `probe-com`, and `probe-storage`.

`probe-com` reports Excel COM/interoperability details and can run safe probe smoke steps with `--smoke-test`. `probe-storage` performs a read-only inventory of likely workbook, template, add-in, autorecovery, and unsaved-file locations; use `--extra-root`, `--recurse`, `--max-files`, and `--include-hashes` when deeper discovery is needed.

## Workflow

1. Use 
px -y workbook-wizard as the executable boundary.
2. Run `info`.
3. Run `check-install` before assuming desktop Excel is available.
4. Run `workbooks` and `current-selection` to identify the active context.
5. Prefer wrapped CLI commands for routine operations.
6. Serialize Excel operations. Desktop COM calls into the same Excel instance can reject concurrent automation.
7. Verify writes by reading touched ranges and saving or exporting artifacts when relevant.

## References

Read `references/cli-reference.md` when choosing commands or when updating this skill as new CLI commands ship.

## Release Notes

- Target Microsoft Excel desktop on Windows only.
- The npm package ships a self-contained Windows C# executable so agents can run `npx -y workbook-wizard` without installing .NET.
- Public skills resolve npm latest with `npx -y workbook-wizard`.
- This rendered public skill is generated from workbook-wizard/skills-src and should not be edited directly.
- Client-side code and compiled binaries should be treated as inspectable. C# raises the effort compared with plain JavaScript, but it is not a strong IP boundary.

