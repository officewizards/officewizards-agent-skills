---
name: onenote-desktop-wizard
description: Safely automate Microsoft OneNote desktop on Windows with direct PowerShell COM and page XML. Use when an agent needs to inspect or change local OneNote notebooks, sections, pages, page XML, tags, embedded files, media, or exported page content.
---

# OneNote Desktop Wizard

Use direct OneNote COM automation for local notebooks, sections, pages, and page XML. Treat page XML and sync state as the primary risk surfaces.

## Operating Rules

- Inspect notebooks, sections, and pages before acting. Identify notebook path/name, section ID, page ID, title, last modified time, and sync/storage context when relevant.
- Prefer explicit notebook/section/page IDs. Avoid active-page fallback for mutations unless the user clearly refers to the active page and you have inspected it first.
- Run one OneNote automation at a time. Desktop COM calls share one OneNote application instance and can reject overlapping work.
- Create a backup or export before destructive page edits, page moves/deletes, embedded-file changes, large XML rewrites, or media extraction.
- Read page XML before writing. Preserve namespace structure and existing content unless the user requested replacement.
- Save or update only when the user requested persistence or the task clearly requires it.
- Never close OneNote or notebooks unless the user explicitly asks. Release COM references without closing the user's application.

## High-Power Actions

Pause and make the risk explicit before page XML rewrites, page deletion/move, embedded file extraction/deletion, media extraction, broad notebook searches, sync-sensitive edits, or changes to shared/cloud-synced notebooks.

## PowerShell Pattern

Use STA PowerShell for COM automation. Attach to OneNote with explicit hierarchy scope, operate on IDs instead of visible titles when mutating, preserve XML namespaces, restore application state in `finally`, and return concise structured output with notebook/section/page IDs, affected titles, before/after summary, exported paths, and warnings.

## Verification

Finish OneNote work by reporting what changed and how it was verified. For XML updates, reread the affected page and confirm the expected title/content elements are present.
