# Excel Wizard CLI Reference

Always pass `-o json` for structured output when a command returns data.

## Commands

### `info`

```bash
npx -y excel-wizard info -o json
```

Reports CLI version, platform, local authentication mode, and whether Excel COM is registered.

### `login`

```bash
npx -y excel-wizard login
```

Initial desktop-only authentication is local. This command exists to preserve a stable MagicPath-style flow and can become a browser login later if hosted features are added.

### `whoami`

```bash
npx -y excel-wizard whoami -o json
```

Reports the current local Windows user and machine identity visible to the CLI.

### `check-install`

```bash
npx -y excel-wizard check-install -o json
```

Checks whether Microsoft Excel desktop COM is registered and whether the CLI can create an Excel automation object.

### `workbooks`

```bash
npx -y excel-wizard workbooks -o json
```

Lists open workbooks with names, paths, save state, and read-only state.

### `current-selection`

```bash
npx -y excel-wizard current-selection -o json
```

Reports the active workbook, worksheet, selection address, and selected value/text when available.

## Boundaries

- Windows desktop Excel only.
- No Excel for web support in this plugin.
- No macOS Excel support in this plugin.
- No localhost server is required for the initial design.
- The private CLI may add more commands without changing the public install repo shape.
