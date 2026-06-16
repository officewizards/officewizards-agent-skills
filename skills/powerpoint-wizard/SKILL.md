<!-- Generated from powerpoint-wizard/skills-src/powerpoint-wizard/SKILL.md.tmpl. Do not edit directly. -->
---
name: powerpoint-wizard
description: Control Microsoft PowerPoint desktop for Windows through the PowerPoint Wizard npx CLI. Use when an agent needs to create, inspect, edit, save, export, or automate PowerPoint presentations, slides, text, pictures, shapes, speaker notes, macros, temporary VBA, or local scripts without browser automation, Microsoft Graph, Office.js add-ins, or raw PowerShell-first workflows.
allowed-tools: Bash(npx -y powerpoint-wizard *)
---

# PowerPoint Wizard

PowerPoint Wizard is a Windows-only CLI for Microsoft PowerPoint desktop automation.

This rendered public skill resolves PowerPoint Wizard from npm latest with npx -y powerpoint-wizard.

Always start by checking what the CLI can do:

```powershell
npx -y powerpoint-wizard help -o json
```

Then inspect the local environment:

```powershell
npx -y powerpoint-wizard info -o json
npx -y powerpoint-wizard check-install -o json
npx -y powerpoint-wizard presentations -o json
```

Create or save presentations through the CLI:

```powershell
npx -y powerpoint-wizard new-presentation --title "Launch Plan" -o json
npx -y powerpoint-wizard save-as --target-path ".\launch-plan.pptx" --force -o json
npx -y powerpoint-wizard save --presentation-path ".\launch-plan.pptx" -o json
```

Use explicit presentation paths when possible:

```powershell
npx -y powerpoint-wizard open-presentation --presentation-path ".\deck.pptx" -o json
npx -y powerpoint-wizard slides --presentation-path ".\deck.pptx" -o json
npx -y powerpoint-wizard read-slide --presentation-path ".\deck.pptx" --slide-index 1 -o json
```

Edit slides and shapes without dropping to VBA:

```powershell
npx -y powerpoint-wizard add-slide --presentation-path ".\deck.pptx" --layout title-content --title "Market" --text "Three launch segments" -o json
npx -y powerpoint-wizard set-slide-title --presentation-path ".\deck.pptx" --slide-index 1 --title "Updated Launch Plan" -o json
npx -y powerpoint-wizard add-textbox --presentation-path ".\deck.pptx" --slide-index 1 --text "Revenue target" --left 72 --top 140 --width 420 --height 80 -o json
npx -y powerpoint-wizard add-picture --presentation-path ".\deck.pptx" --slide-index 1 --image-path ".\chart.png" --left 72 --top 220 --width 560 --height 260 -o json
npx -y powerpoint-wizard set-speaker-notes --presentation-path ".\deck.pptx" --slide-index 1 --notes "Mention the rollout risk." -o json
```

Export through the CLI instead of raw COM when possible:

```powershell
npx -y powerpoint-wizard export-pdf --presentation-path ".\deck.pptx" --target-path ".\deck.pdf" --force -o json
npx -y powerpoint-wizard export-images --presentation-path ".\deck.pptx" --output-dir ".\deck-images" --force -o json
```

Escape hatches are available but execute local code as the current Windows user:

```powershell
npx -y powerpoint-wizard run-macro --presentation-path ".\deck.pptm" --macro-name Module1.Refresh -o json
npx -y powerpoint-wizard run-vba --presentation-path ".\deck.pptm" --vba-code "Public Function Main() As String`nMain = ActivePresentation.Name`nEnd Function" -o json
npx -y powerpoint-wizard run-script --script-path ".\script.ps1" --argument inspect -o json
```

Operational rules:

- Use npx -y powerpoint-wizard as the executable boundary.
- Run `help -o json` when uncertain instead of guessing option names.
- Prefer `--presentation-path` over active-presentation fallback when mutating or exporting.
- Prefer first-party editing commands such as `add-slide`, `add-textbox`, `add-picture`, `set-shape-text`, and `set-speaker-notes` before using escape hatches.
- Treat `run-vba`, `run-macro`, and `run-script` as local-code execution.
- COM automation is serialized by the CLI per PowerPoint application family.
- - This rendered public skill is generated from powerpoint-wizard/skills-src and should not be edited directly.

