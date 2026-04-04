## 1. Update specifications

- [x] 1.1 Add a delta spec for `theme-definitions` that requires var-based `export` entries for all four themes.
- [x] 1.2 Ensure the delta spec preserves the expected resolved export colors for each flavor.

## 2. Update theme files

- [x] 2.1 Replace raw hex values in `themes/catppuccin-latte.json` `export` with `crust`, `base`, and `surface_0`.
- [x] 2.2 Replace raw hex values in `themes/catppuccin-frappe.json` `export` with `crust`, `base`, and `surface_0`.
- [x] 2.3 Replace raw hex values in `themes/catppuccin-macchiato.json` `export` with `crust`, `base`, and `surface_0`.
- [x] 2.4 Replace raw hex values in `themes/catppuccin-mocha.json` `export` with `crust`, `base`, and `surface_0`.

## 3. Verify behavior

- [x] 3.1 Validate the updated theme files still conform to Pi's theme schema.
- [x] 3.2 Confirm the resolved HTML export colors remain unchanged after the migration.
