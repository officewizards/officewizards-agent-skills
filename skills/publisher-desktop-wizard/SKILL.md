---
name: publisher-desktop-wizard
description: Safely automate Microsoft Publisher desktop on Windows with direct PowerShell COM and VBA. Use when an agent needs to inspect or change local Publisher publications, pages, text frames, pictures, linked assets, layout, print settings, macros, PDF output, or other publication exports.
---

# Publisher Desktop Wizard

Use direct PowerShell COM or temporary VBA for local Microsoft Publisher desktop automation. Treat page layout, linked assets, margins, bleed, and print/export settings as visible production state.

## Operating Rules

- Inspect open publications before acting. Identify publication name, full path, saved state, active page, selected shapes/text frames, linked assets, and print/export settings when relevant.
- Prefer explicit publication paths, page numbers, and shape names/IDs. Avoid active-publication fallback for mutations unless the user clearly refers to it and you have inspected it first.
- Run one Publisher automation at a time. Desktop COM calls share one Publisher application instance and can reject overlapping work.
- Create a backup copy before destructive edits, page deletion, layout-wide changes, linked asset changes, print settings changes, macro/VBA changes, or export overwrites.
- Read affected pages, text frames, shapes, pictures, and asset links before writing. Verify afterward by inspecting objects or exporting a preview when layout matters.
- Save/export only when requested or clearly required, and avoid overwriting existing files unless the user asked for that path.
- Never call `Publisher.Application.Quit()` unless the user explicitly asks to close Publisher. Release COM references without closing the user's application.

## High-Power Actions

Pause and make the risk explicit before page deletion, broad text replacement, layout-wide edits, linked asset changes, bleed/margin/print settings changes, macro/VBA execution, or edits to shared/cloud-synced publications.

## PowerShell Pattern

Use STA PowerShell for COM automation. Attach to an existing Publisher instance when possible, operate on explicit pages and shape IDs, preserve print/export settings unless intentionally changing them, restore application state in `finally`, and return concise structured output with publication path, affected pages/shapes, before/after summary, saved/exported paths, and warnings.

## Verification

Finish Publisher work by reporting what changed and how it was verified. For layout, linked assets, print settings, or export work, inspect the object state or exported preview before calling the work done.
