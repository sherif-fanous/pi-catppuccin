# theme-definitions

## Purpose

TBD

## Requirements

### Requirement: Four Catppuccin flavor theme files

The package SHALL provide exactly four theme JSON files at `themes/catppuccin-latte.json`, `themes/catppuccin-frappe.json`, `themes/catppuccin-macchiato.json`, and `themes/catppuccin-mocha.json`.

#### Scenario: All four theme files exist

- **WHEN** the package is installed
- **THEN** the `themes/` directory SHALL contain exactly four files: `catppuccin-latte.json`, `catppuccin-frappe.json`, `catppuccin-macchiato.json`, `catppuccin-mocha.json`

### Requirement: Valid Pi theme schema

Each theme file SHALL be valid against the Pi theme JSON schema and SHALL include the `$schema` field pointing to `https://raw.githubusercontent.com/badlogic/pi-mono/main/packages/coding-agent/src/modes/interactive/theme/theme-schema.json`.

#### Scenario: Schema validation

- **WHEN** a theme file is loaded by Pi
- **THEN** it SHALL pass schema validation with zero errors

### Requirement: Unique theme names

Each theme file SHALL have a unique `name` field matching the pattern `catppuccin-<flavor>` where flavor is one of `latte`, `frappe`, `macchiato`, `mocha`.

#### Scenario: Theme name format

- **WHEN** the `name` field is read from `catppuccin-mocha.json`
- **THEN** the value SHALL be `catppuccin-mocha`

### Requirement: All 51 color tokens defined

Each theme file SHALL define all 51 required Pi color tokens in the `colors` object. No token SHALL be omitted.

#### Scenario: Complete token coverage

- **WHEN** a theme file's `colors` object is inspected
- **THEN** it SHALL contain all 51 tokens: `accent`, `border`, `borderAccent`, `borderMuted`, `success`, `error`, `warning`, `muted`, `dim`, `text`, `thinkingText`, `selectedBg`, `userMessageBg`, `userMessageText`, `customMessageBg`, `customMessageText`, `customMessageLabel`, `toolPendingBg`, `toolSuccessBg`, `toolErrorBg`, `toolTitle`, `toolOutput`, `mdHeading`, `mdLink`, `mdLinkUrl`, `mdCode`, `mdCodeBlock`, `mdCodeBlockBorder`, `mdQuote`, `mdQuoteBorder`, `mdHr`, `mdListBullet`, `toolDiffAdded`, `toolDiffRemoved`, `toolDiffContext`, `syntaxComment`, `syntaxKeyword`, `syntaxFunction`, `syntaxVariable`, `syntaxString`, `syntaxNumber`, `syntaxType`, `syntaxOperator`, `syntaxPunctuation`, `thinkingOff`, `thinkingMinimal`, `thinkingLow`, `thinkingMedium`, `thinkingHigh`, `thinkingXhigh`, `bashMode`

### Requirement: Vars block with palette colors

Each theme file SHALL define a `vars` object containing named entries for all Catppuccin palette colors used in the theme. The `colors` object SHALL reference these var names rather than using raw hex values directly.

#### Scenario: Vars indirection

- **WHEN** the `colors.accent` value is read from a theme file
- **THEN** it SHALL be a string matching a key in the `vars` object (e.g., `"mauve"`) rather than a raw hex value

### Requirement: Exact Catppuccin palette hex values

All hex values in the `vars` block SHALL match exactly the values from Catppuccin palette v1.7.1 for the corresponding flavor and color name.

#### Scenario: Mocha Blue accuracy

- **WHEN** the `vars.blue` value is read from `catppuccin-mocha.json`
- **THEN** the value SHALL be `#89b4fa`

#### Scenario: Latte Base accuracy

- **WHEN** the `vars.base` value is read from `catppuccin-latte.json`
- **THEN** the value SHALL be `#eff1f5`

### Requirement: Style Guide compliant color mappings

Color token assignments SHALL follow the Catppuccin Style Guide and VS Code markdown token definitions as documented in the design. Specifically:

- `success` → Green, `error` → Red, `warning` → Yellow (Style Guide:Typography)
- `syntaxKeyword` → Mauve, `syntaxFunction` → Blue, `syntaxString` → Green (Style Guide:Code Editors)
- `mdHeading` → Red, `mdCode` → Green, `mdQuote` → Pink (VS Code Catppuccin markdown tokens)
- `toolDiffAdded` → Green, `toolDiffRemoved` → Red (Style Guide:Diff & Merge)

#### Scenario: Syntax keyword mapping

- **WHEN** `colors.syntaxKeyword` is resolved through `vars`
- **THEN** it SHALL resolve to the flavor's Mauve hex value

#### Scenario: Markdown heading mapping

- **WHEN** `colors.mdHeading` is resolved through `vars`
- **THEN** it SHALL resolve to the flavor's Red hex value

### Requirement: No empty-string token values

Every color token in the `colors` object SHALL resolve to an explicit Catppuccin palette color via the `vars` block. No token SHALL use `""` (empty string / terminal default).

#### Scenario: All tokens are explicit

- **WHEN** all 51 values in a theme file's `colors` object are inspected
- **THEN** every value SHALL be a non-empty string matching a key in the `vars` object

### Requirement: HTML export section

Each theme file SHALL include an `export` object with `pageBg`, `cardBg`, and `infoBg` keys, using the flavor's Crust, Base, and Surface 0 hex values respectively.

#### Scenario: Mocha export colors

- **WHEN** the `export` object is read from `catppuccin-mocha.json`
- **THEN** `pageBg` SHALL be `#11111b`, `cardBg` SHALL be `#1e1e2e`, `infoBg` SHALL be `#313244`

#### Scenario: Latte export colors

- **WHEN** the `export` object is read from `catppuccin-latte.json`
- **THEN** `pageBg` SHALL be `#dce0e8`, `cardBg` SHALL be `#eff1f5`, `infoBg` SHALL be `#ccd0da`
