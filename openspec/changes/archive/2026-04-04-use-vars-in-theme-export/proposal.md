## Why

The Catppuccin theme files currently duplicate export colors as raw hex values even though the same colors already exist in each theme's `vars` palette. Pi's current implementation resolves variable references inside the optional `export` section, so the themes can now express those export colors through the palette instead of repeating literals.

## What Changes

- Update the four Catppuccin theme files to reference `vars` entries in their `export` sections instead of hard-coded hex values.
- Align the HTML export color definitions with the same palette indirection already used throughout each theme's `colors` section.
- Update the theme specification to require var-based `export` entries rather than raw hex literals.

## Capabilities

### New Capabilities

- None.

### Modified Capabilities

- `theme-definitions`: Change the HTML export requirement so `export.pageBg`, `export.cardBg`, and `export.infoBg` reference palette vars (`crust`, `base`, and `surface_0`) while preserving the same resolved colors.

## Impact

- Affected files: `themes/catppuccin-latte.json`, `themes/catppuccin-frappe.json`, `themes/catppuccin-macchiato.json`, `themes/catppuccin-mocha.json`
- Affected spec: `openspec/specs/theme-definitions/spec.md`
- No API changes, dependency changes, or visual output changes are expected; this is a representation cleanup with equivalent resolved colors.
