---
name: powerpoint-desktop-wizard
description: Safely automate Microsoft PowerPoint desktop on Windows with direct PowerShell COM and VBA. Use when an agent needs to inspect or change local PowerPoint presentations, slides, shapes, text, pictures, speaker notes, macros, exports, or the active presentation.
---

# PowerPoint Desktop Wizard

Use direct PowerShell COM or temporary VBA for local Microsoft PowerPoint desktop automation. Keep edits targeted, inspect before mutating, and verify visible presentation state after changes.

Before mutating or transmitting data, read and follow the shared [Office automation safety policy](../officewizards/references/office-safety.md).

## Operating Rules

- Inspect open presentations before acting. Identify presentation name, full path, saved state, active slide, and selected shape when relevant.
- Prefer explicit presentation paths or names. Avoid active-presentation fallback for mutations unless the user clearly refers to the active presentation and you have inspected it first.
- Run one PowerPoint automation at a time. Desktop COM calls share one PowerPoint application instance and can reject overlapping work.
- Read the affected slide, shape, text, notes, or media object before writing. After writing, inspect it again or export a preview artifact when visual verification matters.
- Save when the user requested persistence or the task clearly requires a saved output. Do not ask again when the target and requested persistence are clear.
- Export PDFs or images only when requested or required by the task, and avoid overwriting existing files unless the user asked for that path.
- Never call `PowerPoint.Application.Quit()` unless the user explicitly asks to close PowerPoint. Release COM references without closing the user's application.

## PowerShell Pattern

Use STA PowerShell for COM automation. Attach to an existing PowerPoint instance when possible, use explicit slide indexes and shape names after inspection, restore application state in `finally`, and return concise structured output with presentation path, affected slides/shapes, before/after summary, saved/exported paths, and warnings.

## Verification

Finish PowerPoint work by reporting what changed and how it was verified. If layout or visual quality matters, inspect the slide or exported preview before calling the work done.
