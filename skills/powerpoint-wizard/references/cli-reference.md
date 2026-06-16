<!-- Generated from powerpoint-wizard/skills-src/powerpoint-wizard/references/cli-reference.md.tmpl. Do not edit directly. -->
# PowerPoint Wizard CLI Reference

Package: `powerpoint-wizard`
Version: `0.1.0`
Channel: `public`

Base command:

```powershell
npx -y powerpoint-wizard
```

Core discovery:

```powershell
npx -y powerpoint-wizard help -o json
npx -y powerpoint-wizard help read-slide -o json
npx -y powerpoint-wizard info -o json
npx -y powerpoint-wizard check-install -o json
```

Presentation workflow:

```powershell
npx -y powerpoint-wizard presentations -o json
npx -y powerpoint-wizard new-presentation --title "Launch Plan" -o json
npx -y powerpoint-wizard open-presentation --presentation-path ".\deck.pptx" -o json
npx -y powerpoint-wizard presentation-info --presentation-path ".\deck.pptx" -o json
npx -y powerpoint-wizard slides --presentation-path ".\deck.pptx" -o json
npx -y powerpoint-wizard read-slide --presentation-path ".\deck.pptx" --slide-index 1 -o json
npx -y powerpoint-wizard add-slide --presentation-path ".\deck.pptx" --layout title-content --title "Market" --text "Three launch segments" -o json
npx -y powerpoint-wizard add-textbox --presentation-path ".\deck.pptx" --slide-index 1 --text "Revenue target" --left 72 --top 140 --width 420 --height 80 -o json
npx -y powerpoint-wizard add-picture --presentation-path ".\deck.pptx" --slide-index 1 --image-path ".\chart.png" --left 72 --top 220 --width 560 --height 260 -o json
npx -y powerpoint-wizard set-speaker-notes --presentation-path ".\deck.pptx" --slide-index 1 --notes "Mention rollout risk." -o json
npx -y powerpoint-wizard save-as --presentation-path ".\deck.pptx" --target-path ".\copy.pptx" --force -o json
npx -y powerpoint-wizard export-pdf --presentation-path ".\deck.pptx" --target-path ".\deck.pdf" --force -o json
npx -y powerpoint-wizard export-images --presentation-path ".\deck.pptx" --output-dir ".\images" --force -o json
```

