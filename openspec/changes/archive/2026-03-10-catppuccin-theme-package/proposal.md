## Why

The Pi Coding Agent ships with only two built-in themes (`dark` and `light`). Users who rely on the Catppuccin color scheme across their development toolchain (terminal, editor, tmux, etc.) have no first-party option for a consistent Pi experience. A community-standard Catppuccin theme package covering all four official flavors fills this gap and serves as a high-quality reference implementation for Pi theme package authors.

## What Changes

- Introduce a new Pi package (`@sherif-fanous/pi-catppuccin`) that provides **four** theme JSON files — one per official Catppuccin flavor:
  - **Latte** (light)
  - **Frappé** (dark)
  - **Macchiato** (dark)
  - **Mocha** (dark)
- Each theme defines all 51 required Pi color tokens using exact hex values from the [Catppuccin palette v1.7.1](https://github.com/catppuccin/palette), mapped according to the [Catppuccin Style Guide](https://github.com/catppuccin/catppuccin/blob/main/docs/style-guide.md) and the [Catppuccin VS Code markdown token definitions](https://github.com/catppuccin/vscode/blob/main/packages/catppuccin-vsc/src/theme/tokens/markdown.ts).
- Ship repository scaffolding (`package.json`, `README.md`, `LICENSE`, `CHANGELOG.md`, `.gitignore`, `.npmignore`) following the [Pi Packages](https://github.com/badlogic/pi-mono/blob/main/packages/coding-agent/docs/packages.md) conventions.
- Include optional HTML export colors derived from the flavor's base/mantle/surface palette.

## Capabilities

### New Capabilities

- `theme-definitions`: Defines the four Catppuccin flavor theme JSON files with all 51 Pi color tokens, vars, and export section, following the Pi theme schema.
- `package-scaffolding`: Provides the npm-publishable package structure (`package.json` with `pi.themes`, `README.md`, `LICENSE`, `CHANGELOG.md`, `.gitignore`, `.npmignore`) conforming to Pi Package conventions.

### Modified Capabilities

_None — this is a greenfield package with no existing specs._

## Impact

- **New files**: `themes/catppuccin-latte.json`, `themes/catppuccin-frappe.json`, `themes/catppuccin-macchiato.json`, `themes/catppuccin-mocha.json`, `package.json`, `README.md`, `LICENSE`, `CHANGELOG.md`, `.gitignore`, `.npmignore`.
- **Dependencies**: Zero runtime dependencies. Only `peerDependencies` on `@mariozechner/pi-coding-agent` (range `"*"`).
- **Distribution**: Published to npm as `@sherif-fanous/pi-catppuccin`; installable via `pi install npm:@sherif-fanous/pi-catppuccin`.
- **No breaking changes** to any existing system — purely additive.
