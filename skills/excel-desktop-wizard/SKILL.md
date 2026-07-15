---
name: excel-desktop-wizard
description: Safely automate Microsoft Excel desktop on Windows with direct PowerShell COM and VBA. Use when an agent needs to inspect or change local Excel workbooks, worksheets, ranges, formulas, charts, tables, macros, exports, or the current Excel selection.
---

# Excel Desktop Wizard

Use direct PowerShell COM or temporary VBA for local Microsoft Excel desktop automation. Keep automation specific to the user's workbook and verify results from Excel.

Before mutating or transmitting data, read and follow the shared [Office automation safety policy](../officewizards/references/office-safety.md).

## Operating Rules

- Inspect open workbooks before acting. Identify workbook name, full path, saved state, active sheet, and selection when relevant.
- Prefer explicit workbook paths or names. Avoid active-workbook fallback for mutations unless the user clearly refers to the active workbook and you have inspected it first.
- Run one Excel automation at a time. Desktop COM calls share one Excel application instance and can reject overlapping work.
- Read the affected range, sheet, or object before writing. After writing, read it back or inspect the output artifact to verify the result.
- Save when the user requested persistence or the task clearly requires a saved output. Do not ask again when the target and requested persistence are clear.
- Export files only when requested or required by the task, and avoid overwriting existing files unless the user asked for that path.
- Never call `Excel.Application.Quit()` unless the user explicitly asks to close Excel. Release COM references without closing the user's application.

## PowerShell Pattern

Use STA PowerShell for COM automation. Attach to an existing Excel instance when possible, restore application state in `finally`, prefer rectangular array writes over cell-by-cell loops, and return concise structured output with workbook path, sheet, affected address, before/after summary, saved/exported paths, and warnings.

## Verification

Finish Excel work by reporting what changed and how it was verified. If verification could not be completed, say exactly what remains uncertain and leave the workbook in the safest useful state.
