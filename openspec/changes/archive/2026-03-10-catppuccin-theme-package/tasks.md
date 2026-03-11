## 1. Package Scaffolding

- [x] 1.1 Create `package.json` with name `@sherif-fanous/pi-catppuccin`, `pi-package` keyword, `pi.themes: ["./themes"]`, peer dependency on `@mariozechner/pi-coding-agent`, and `files` array
- [x] 1.2 Create `LICENSE` with MIT license, copyright 2026 Sherif Fanous
- [x] 1.3 Create `README.md` with package description, install/try/uninstall commands, and list of four theme names
- [x] 1.4 Create `CHANGELOG.md` with initial `[0.1.0]` release entry
- [x] 1.5 Create `.gitignore` excluding `node_modules/` and workspace file
- [x] 1.6 Create `.npmignore` excluding workspace file

## 2. Theme Files

- [x] 2.1 Create `themes/` directory
- [x] 2.2 Create `themes/catppuccin-latte.json` with all 51 color tokens, vars block with Latte palette hex values, and export section
- [x] 2.3 Create `themes/catppuccin-frappe.json` with all 51 color tokens, vars block with Frappé palette hex values, and export section
- [x] 2.4 Create `themes/catppuccin-macchiato.json` with all 51 color tokens, vars block with Macchiato palette hex values, and export section
- [x] 2.5 Create `themes/catppuccin-mocha.json` with all 51 color tokens, vars block with Mocha palette hex values, and export section

## 3. Verification

- [x] 3.1 Verify each theme JSON is valid JSON and contains exactly 51 color tokens in the `colors` object
- [x] 3.2 Verify all hex values in `vars` blocks match Catppuccin palette v1.7.1
- [x] 3.3 Verify all `colors` values reference valid `vars` keys or use `""` for terminal default
- [x] 3.4 Verify `$schema` field is present in each theme file
- [x] 3.5 Verify `name` field matches `catppuccin-<flavor>` pattern in each theme file
