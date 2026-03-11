## ADDED Requirements

### Requirement: Valid package.json with Pi manifest

The `package.json` SHALL declare the package name as `@sherif-fanous/pi-catppuccin`, include the `pi-package` keyword for gallery discoverability, and declare `pi.themes: ["./themes"]` for automatic theme discovery.

#### Scenario: Package name and keywords
- **WHEN** `package.json` is parsed
- **THEN** `name` SHALL be `@sherif-fanous/pi-catppuccin` and `keywords` SHALL include `pi-package`

#### Scenario: Pi manifest
- **WHEN** Pi loads the package
- **THEN** the `pi.themes` array SHALL contain `"./themes"` causing Pi to discover all `.json` files in the `themes/` directory

### Requirement: Peer dependency on Pi coding agent

The `package.json` SHALL list `@mariozechner/pi-coding-agent` as a peer dependency with range `"*"`. The package SHALL have zero runtime `dependencies`.

#### Scenario: Dependency declarations
- **WHEN** `package.json` is inspected
- **THEN** `peerDependencies` SHALL contain `"@mariozechner/pi-coding-agent": "*"` and `dependencies` SHALL be absent or empty

### Requirement: Files field for npm publishing

The `package.json` `files` array SHALL include `themes/`, `README.md`, `LICENSE`, and `CHANGELOG.md` to ensure only necessary files are published to npm.

#### Scenario: Published file list
- **WHEN** `npm pack` is run
- **THEN** the tarball SHALL contain the four theme JSON files, `README.md`, `LICENSE`, `CHANGELOG.md`, and `package.json`

### Requirement: README with install instructions

The `README.md` SHALL include the package description, installation instructions using `pi install npm:@sherif-fanous/pi-catppuccin`, a try-without-installing command using `pi -e`, an uninstall command, and a list of the four available theme names.

#### Scenario: Install command documented
- **WHEN** a user reads `README.md`
- **THEN** they SHALL find the command `pi install npm:@sherif-fanous/pi-catppuccin`

#### Scenario: Theme names listed
- **WHEN** a user reads `README.md`
- **THEN** they SHALL find all four theme names: `catppuccin-latte`, `catppuccin-frappe`, `catppuccin-macchiato`, `catppuccin-mocha`

### Requirement: MIT License

The `LICENSE` file SHALL contain a valid MIT License with copyright holder "Sherif Fanous" and year 2026.

#### Scenario: License content
- **WHEN** `LICENSE` is read
- **THEN** it SHALL contain "MIT License" and "Copyright (c) 2026 Sherif Fanous"

### Requirement: Changelog

The `CHANGELOG.md` SHALL document the initial release as version `0.1.0` with a brief description.

#### Scenario: Initial changelog entry
- **WHEN** `CHANGELOG.md` is read
- **THEN** it SHALL contain an entry for `[0.1.0]` describing the initial release

### Requirement: Git and npm ignore files

The `.gitignore` SHALL exclude `node_modules/` and the VS Code workspace file. The `.npmignore` SHALL exclude the VS Code workspace file.

#### Scenario: Gitignore content
- **WHEN** `.gitignore` is read
- **THEN** it SHALL include `node_modules/` and the workspace file pattern

#### Scenario: Npmignore content
- **WHEN** `.npmignore` is read
- **THEN** it SHALL include the workspace file pattern
