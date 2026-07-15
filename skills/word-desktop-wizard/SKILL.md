---
name: word-desktop-wizard
description: Safely automate Microsoft Word desktop on Windows with direct PowerShell COM and VBA. Use when an agent needs to inspect or change local Word documents, text, tables, styles, comments, tracked changes, sections, headers, footers, fields, macros, or exports.
---

# Word Desktop Wizard

Use direct PowerShell COM or temporary VBA for local Microsoft Word desktop automation. Treat document structure as fragile: visible text, revisions, fields, sections, and styles can interact in surprising ways.

Before mutating or transmitting data, read and follow the shared [Office automation safety policy](../officewizards/references/office-safety.md).

## Operating Rules

- Inspect open documents before acting. Identify document name, full path, saved state, protection state, track-changes state, and selection when relevant.
- Prefer explicit document paths or names. Avoid active-document fallback for mutations unless the user clearly refers to the active document and you have inspected it first.
- Run one Word automation at a time. Desktop COM calls share one Word application instance and can reject overlapping work.
- Read the affected range, table, style, comment, field, header, or footer before writing. Verify afterward by reading the updated object or exporting/inspecting output when layout matters.
- Save when the user requested persistence or the task clearly requires a saved output. Do not ask again when the target and requested persistence are clear.
- Export PDFs only when requested or required by the task, and avoid overwriting existing files unless the user asked for that path.
- Never call `Word.Application.Quit()` unless the user explicitly asks to close Word. Release COM references without closing the user's application.

## PowerShell Pattern

Use STA PowerShell for COM automation. Attach to an existing Word instance when possible, use explicit ranges instead of relying on selection, preserve track-changes and display-alert settings, restore application state in `finally`, and return concise structured output with document path, affected ranges/objects, before/after summary, saved/exported paths, and warnings.

## Verification

Finish Word work by reporting what changed and how it was verified. For layout, tracked changes, comments, or fields, inspect the relevant document objects before calling the work done.
