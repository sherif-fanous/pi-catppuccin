# Changelog

This changelog follows [Common Changelog](https://common-changelog.org/).

## [0.3.0] - 2026-10-13

### Changed

- Map thinking levels to the reversed Catppuccin rainbow, from Lavender at `minimal` to Red at `max` ([`caea4a5`](https://github.com/sherif-fanous/pi-catppuccin/commit/caea4a5))
- Use Pink for the bash mode border so it no longer matches a thinking level ([`27471c1`](https://github.com/sherif-fanous/pi-catppuccin/commit/27471c1))

### Added

- Declare `appearance` so Pi pairs Latte with light terminals and the other flavors with dark terminals ([`bcb7833`](https://github.com/sherif-fanous/pi-catppuccin/commit/bcb7833))
- Define scrollbar and transcript search colors instead of relying on Pi's fallbacks ([`bcb7833`](https://github.com/sherif-fanous/pi-catppuccin/commit/bcb7833))

### Fixed

- Fix unreadable text on selected items by using Surface 1 for `selectedBg` ([`e430b19`](https://github.com/sherif-fanous/pi-catppuccin/commit/e430b19))
- Point `$schema` to `https://pi.dev/schemas/theme.schema.json`, as the previous URL no longer resolves ([`99e79af`](https://github.com/sherif-fanous/pi-catppuccin/commit/99e79af))

## [0.2.0] - 2026-04-04

### Changed

- Reference theme vars in `export` sections instead of repeating hex values ([`bdbdf94`](https://github.com/sherif-fanous/pi-catppuccin/commit/bdbdf94))

### Removed

- Remove the unneeded `@mariozechner/pi-coding-agent` peer dependency ([`2ebf75c`](https://github.com/sherif-fanous/pi-catppuccin/commit/2ebf75c))

### Fixed

- Fix the uninstall command in the README ([`df68a86`](https://github.com/sherif-fanous/pi-catppuccin/commit/df68a86))

## [0.1.0] - 2026-03-10

_Initial release._

[0.3.0]: https://github.com/sherif-fanous/pi-catppuccin/releases/tag/v0.3.0
[0.2.0]: https://github.com/sherif-fanous/pi-catppuccin/releases/tag/v0.2.0
[0.1.0]: https://github.com/sherif-fanous/pi-catppuccin/releases/tag/v0.1.0
