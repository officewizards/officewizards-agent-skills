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
npx -y powerpoint-wizard open-presentation --presentation-path ".\deck.pptx" -o json
npx -y powerpoint-wizard presentation-info --presentation-path ".\deck.pptx" -o json
npx -y powerpoint-wizard slides --presentation-path ".\deck.pptx" -o json
npx -y powerpoint-wizard read-slide --presentation-path ".\deck.pptx" --slide-index 1 -o json
npx -y powerpoint-wizard export-pdf --presentation-path ".\deck.pptx" --target-path ".\deck.pdf" --force -o json
npx -y powerpoint-wizard export-images --presentation-path ".\deck.pptx" --output-dir ".\images" --force -o json
```


