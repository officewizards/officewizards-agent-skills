---
name: outlook-desktop-wizard
description: Safely automate Microsoft Outlook desktop on Windows with direct PowerShell COM and VBA. Use when an agent needs to inspect or change local Outlook mail, calendar events, contacts, tasks, folders, attachments, drafts, rules, or account-visible Outlook data.
---

# Outlook Desktop Wizard

Use direct PowerShell COM or temporary VBA for local Microsoft Outlook desktop automation. Outlook automation touches live communication and calendar data, so use the strictest confirmation and verification posture.

## Operating Rules

- Inspect stores, accounts, folders, and candidate items before acting. Identify item IDs, subjects, dates, recipients, organizer, folder path, unread state, and attachment names when relevant.
- Prefer explicit folder paths and stable item identifiers. Avoid active-item or selected-item fallback for mutations unless the user clearly refers to that item and you have inspected it first.
- Run one Outlook automation at a time. Desktop COM calls share one Outlook application/session and can reject overlapping work.
- Create drafts instead of sending whenever possible. Never send, delete, move, archive, invite, respond, forward, mark read/unread, or change recipients without explicit user intent and pre-action inspection.
- Treat mailbox, calendar, contact, and task data as sensitive. Keep terminal output minimal and avoid dumping message bodies unless needed for the task.
- Save changes only when the user requested persistence or the task clearly requires it. Prefer draft and review workflows for outbound communication.
- Never call `Outlook.Application.Quit()` unless the user explicitly asks to close Outlook. Release COM references without closing the user's application.

## High-Power Actions

Pause and make the risk explicit before sending mail, sending invites, deleting/moving/archive operations, bulk folder operations, rule changes, attachment export, contact edits, task completion, calendar recurrence edits, or mailbox-wide searches.

## PowerShell Pattern

Use STA PowerShell for COM automation. Attach to an existing Outlook instance when possible, use namespace/store/folder/item objects explicitly, inspect recipients and bodies before outbound actions, restore application state in `finally`, and return concise structured output with item IDs, folder paths, affected items, draft/save status, and warnings.

## Verification

Finish Outlook work by reporting what changed and how it was verified. For outbound drafts or meetings, report recipients, subject, location/time, and draft state without sending unless the user explicitly requested send.
