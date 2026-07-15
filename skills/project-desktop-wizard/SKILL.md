---
name: project-desktop-wizard
description: Safely automate Microsoft Project desktop on Windows with direct PowerShell COM and VBA. Use when an agent needs to inspect or change local Project plans, tasks, resources, assignments, dependencies, calendars, baselines, views, reports, macros, or exports.
---

# Project Desktop Wizard

Use direct PowerShell COM or temporary VBA for local Microsoft Project desktop automation. Treat schedule calculations, calendars, baselines, and resource leveling as high-impact project state.

Before mutating or transmitting data, read and follow the shared [Office automation safety policy](../officewizards/references/office-safety.md).

## Operating Rules

- Inspect open projects before acting. Identify project name, full path, saved state, calculation mode, active view, selected tasks/resources, and baseline state when relevant.
- Prefer explicit project paths, task IDs, resource IDs, and assignment IDs. Avoid active-project fallback for mutations unless the user clearly refers to it and you have inspected it first.
- Run one Project automation at a time. Desktop COM calls share one Project application instance and can reject overlapping work.
- Read affected tasks, dependencies, resources, assignments, and calendars before writing. Verify afterward with the changed IDs, dates, durations, and dependency/resource summaries.
- Save/export only when requested or clearly required, and avoid overwriting existing files unless the user asked for that path.
- Never call `MSProject.Application.Quit()` unless the user explicitly asks to close Project. Release COM references without closing the user's application.

## PowerShell Pattern

Use STA PowerShell for COM automation. Attach to an existing Project instance when possible, operate on explicit IDs, preserve calculation/alert settings unless intentionally changing them, restore application state in `finally`, and return concise structured output with project path, affected task/resource IDs, before/after schedule summary, saved/exported paths, and warnings.

## Verification

Finish Project work by reporting what changed and how it was verified. For schedule-impacting changes, include the before/after task IDs, dates, durations, dependencies, resources, and whether recalculation occurred.
