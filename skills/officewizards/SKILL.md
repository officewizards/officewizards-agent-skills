---
name: officewizards
description: Route Microsoft Office desktop automation requests to the right Office Wizards product skill. Use when a user mentions Office Wizards, Microsoft Office desktop apps, Excel, Word, PowerPoint, Outlook, or local Windows Office automation and the exact product skill should be selected.
user-invocable: true
---

# Office Wizards

Office Wizards is a suite of agent-facing skills backed by product CLIs for Microsoft Office desktop apps.

Use the narrowest sibling skill that matches the target app:

- Excel desktop, workbooks, worksheets, ranges, formulas, charts, tables, macros, VBA, CSV import, PDF export, or the current Excel selection: use [workbook-wizard](../workbook-wizard/SKILL.md).
- Word desktop: reserved for a future `doc-wizard` skill.
- PowerPoint desktop: reserved for a future `deck-wizard` skill.
- Outlook desktop: reserved for a future `inbox-wizard` skill.

If the user asks for Excel work, route directly to `workbook-wizard`. Do not use browser automation, Office.js, Microsoft Graph, or raw PowerShell as the first path when an Office Wizards product skill exists for the desktop app.
