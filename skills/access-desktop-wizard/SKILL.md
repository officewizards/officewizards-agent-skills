---
name: access-desktop-wizard
description: Safely automate Microsoft Access desktop on Windows with direct PowerShell COM, DAO, ADO, and VBA. Use when an agent needs to inspect or change local Access databases, tables, queries, forms, reports, macros, modules, imports, exports, or linked data.
---

# Access Desktop Wizard

Use direct Access COM, DAO, ADO, or temporary VBA for local Microsoft Access desktop automation. Treat databases as stateful files where schema and action queries can cause irreversible changes.

## Operating Rules

- Inspect open databases and target files before acting. Identify database path, lock-file state, linked tables, object names, and whether users may have the file open.
- Prefer explicit database paths and object names. Avoid active-database fallback for mutations unless the user clearly refers to it and you have inspected it first.
- Run one Access automation at a time. Desktop COM calls share one Access application instance and can reject overlapping work.
- Create a full database backup before schema changes, data updates/deletes, action queries, macro/VBA changes, imports, linked-table changes, or compact/repair.
- Read table/query definitions or sample rows before writing. Verify afterward with row counts, schema inspection, or exported artifacts.
- Save object changes only when the user requested persistence or the task clearly requires it.
- Never call `Access.Application.Quit()` unless the user explicitly asks to close Access. Release COM references without closing the user's application.

## High-Power Actions

Pause and make the risk explicit before action queries, schema changes, table deletes, compact/repair, linked-table relinking, macro/VBA execution, broad imports/exports, or edits while lock files suggest active users.

## PowerShell Pattern

Use STA PowerShell for COM automation. Attach to an existing Access instance when possible, use explicit database/object references, prefer transactions for data changes when available, restore application state in `finally`, and return concise structured output with database path, affected objects, row counts/schema summary, backup path, and warnings.

## Verification

Finish Access work by reporting what changed and how it was verified. For destructive or schema work, include the backup path and the verification query or object inspection used.
