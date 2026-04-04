## MODIFIED Requirements

### Requirement: HTML export section

Each theme file SHALL include an `export` object with `pageBg`, `cardBg`, and `infoBg` keys. These keys SHALL reference the flavor's `crust`, `base`, and `surface_0` entries from the theme's `vars` object respectively, and SHALL therefore resolve to the same export colors as before.

#### Scenario: Mocha export vars

- **WHEN** the `export` object is read from `catppuccin-mocha.json`
- **THEN** `pageBg` SHALL be `"crust"`, `cardBg` SHALL be `"base"`, and `infoBg` SHALL be `"surface_0"`

#### Scenario: Latte export vars

- **WHEN** the `export` object is read from `catppuccin-latte.json`
- **THEN** `pageBg` SHALL be `"crust"`, `cardBg` SHALL be `"base"`, and `infoBg` SHALL be `"surface_0"`

#### Scenario: Resolved export colors remain unchanged

- **WHEN** Pi resolves the `export` object through the theme's `vars`
- **THEN** the resulting colors SHALL remain `#11111b`, `#1e1e2e`, and `#313244` for Mocha; `#232634`, `#303446`, and `#414559` for Frappe; `#181926`, `#24273a`, and `#363a4f` for Macchiato; and `#dce0e8`, `#eff1f5`, and `#ccd0da` for Latte
