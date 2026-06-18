---
name: visio-desktop-wizard
description: Safely automate Microsoft Visio desktop on Windows with direct PowerShell COM and VBA. Use when an agent needs to inspect or change local Visio drawings, pages, shapes, connectors, masters, stencils, layers, layout, exports, or diagram metadata.
---

# Visio Desktop Wizard

Use direct PowerShell COM or temporary VBA for local Microsoft Visio desktop automation. Treat layout, shape geometry, masters, and connector routing as fragile visible state.

## Operating Rules

- Inspect open documents before acting. Identify drawing name, full path, saved state, active page, selected shapes, stencils, and masters when relevant.
- Prefer explicit drawing paths, page names, and shape IDs/names. Avoid active-document fallback for mutations unless the user clearly refers to it and you have inspected it first.
- Run one Visio automation at a time. Desktop COM calls share one Visio application instance and can reject overlapping work.
- Create a backup copy before destructive edits, page deletion, master/stencil edits, connector rerouting, layout changes, or macro/VBA changes.
- Read affected pages, shapes, connectors, and geometry before writing. Verify afterward by inspecting objects or exporting a preview when visual layout matters.
- Save/export only when requested or clearly required, and avoid overwriting existing files unless the user asked for that path.
- Never call `Visio.Application.Quit()` unless the user explicitly asks to close Visio. Release COM references without closing the user's application.

## High-Power Actions

Pause and make the risk explicit before page deletion, master edits, connector rerouting, automatic layout, shape geometry changes, stencil changes, macro/VBA execution, or edits to shared/cloud-synced diagrams.

## PowerShell Pattern

Use STA PowerShell for COM automation. Attach to an existing Visio instance when possible, operate on explicit page and shape IDs, preserve formulas/ShapeSheet state unless intentionally changing it, restore application state in `finally`, and return concise structured output with drawing path, affected pages/shapes, before/after summary, exported paths, and warnings.

## Verification

Finish Visio work by reporting what changed and how it was verified. For geometry or layout work, inspect shape positions/connectors or export a preview before calling the work done.
