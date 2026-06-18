---
name: officewizards
description: Route Microsoft Office desktop automation requests to the right Office Wizards desktop wizard skill. Use when a user mentions Office Wizards, Microsoft Office desktop apps, Excel, PowerPoint, Word, Outlook, OneNote, Access, Visio, Project, Publisher, or local Windows Office automation and the exact app-specific guidance skill should be selected.
---

# Office Wizards

Office Wizards is a suite of agent-facing desktop wizard skills for Microsoft Office automation on Windows.

Use the narrowest sibling skill that matches the target app:

- Excel desktop, workbooks, worksheets, ranges, formulas, charts, tables, macros, VBA, CSV import, PDF export, or the current Excel selection: use [excel-desktop-wizard](../excel-desktop-wizard/SKILL.md).
- PowerPoint desktop, presentations, slides, shapes, speaker notes, exports, macros, or VBA: use [powerpoint-desktop-wizard](../powerpoint-desktop-wizard/SKILL.md).
- Word desktop, documents, comments, tracked changes, styles, tables, headers, footers, fields, macros, or PDF export: use [word-desktop-wizard](../word-desktop-wizard/SKILL.md).
- Outlook desktop, mail, calendar events, contacts, tasks, folders, attachments, drafts, or rules: use [outlook-desktop-wizard](../outlook-desktop-wizard/SKILL.md).
- OneNote desktop, notebooks, sections, pages, page XML, tags, embedded files, media, or exports: use [onenote-desktop-wizard](../onenote-desktop-wizard/SKILL.md).
- Access desktop, databases, tables, queries, forms, reports, macros, modules, imports, exports, or linked data: use [access-desktop-wizard](../access-desktop-wizard/SKILL.md).
- Visio desktop, drawings, pages, shapes, connectors, masters, stencils, layers, layout, or exports: use [visio-desktop-wizard](../visio-desktop-wizard/SKILL.md).
- Project desktop, project plans, tasks, resources, assignments, dependencies, calendars, baselines, views, reports, or exports: use [project-desktop-wizard](../project-desktop-wizard/SKILL.md).
- Publisher desktop, publications, pages, text frames, pictures, linked assets, layout, print settings, or PDF output: use [publisher-desktop-wizard](../publisher-desktop-wizard/SKILL.md).

Do not duplicate the sibling skill instructions here. Route to the matching skill, then follow that skill's desktop COM safety workflow.

Use browser automation, Microsoft Graph, Office.js, or cloud APIs only when the user explicitly asks for those surfaces or desktop Office is not the right target.
