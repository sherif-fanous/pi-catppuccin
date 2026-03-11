## Context

Pi themes are JSON files that define 51 color tokens covering Core UI, Backgrounds & Content, Markdown, Tool Diffs, Syntax Highlighting, Thinking Level Borders, and Bash Mode. Themes are loaded from a `themes/` directory declared in `package.json` under the `pi` key and distributed via npm or git as Pi Packages.

Catppuccin is a community-driven pastel color scheme with four official flavors — Latte (light), Frappé (dark), Macchiato (dark), and Mocha (dark). Its [Style Guide](https://github.com/catppuccin/catppuccin/blob/main/docs/style-guide.md) provides authoritative mappings for backgrounds, typography, code editor syntax, diff, and general UI. Where the style guide has no markdown-specific guidance, the [Catppuccin VS Code extension's markdown token definitions](https://github.com/catppuccin/vscode/blob/main/packages/catppuccin-vsc/src/theme/tokens/markdown.ts) provide the canonical reference. All hex values are sourced from the [Catppuccin palette v1.7.1](https://github.com/catppuccin/palette/blob/main/palette.json).

### References

1. [Pi Themes Documentation](https://github.com/badlogic/pi-mono/blob/main/packages/coding-agent/docs/themes.md)
2. [Pi Packages Documentation](https://github.com/badlogic/pi-mono/blob/main/packages/coding-agent/docs/packages.md)
3. [Catppuccin Palette v1.7.1](https://github.com/catppuccin/palette/blob/main/palette.json)
4. [Catppuccin Style Guide](https://github.com/catppuccin/catppuccin/blob/main/docs/style-guide.md)
5. [Catppuccin VS Code Markdown Tokens](https://github.com/catppuccin/vscode/blob/main/packages/catppuccin-vsc/src/theme/tokens/markdown.ts)

## Goals / Non-Goals

**Goals:**

- Provide all four Catppuccin flavors as installable Pi themes with pixel-perfect palette accuracy.
- Map every one of the 51 required Pi color tokens to the appropriate Catppuccin palette color, citing the authoritative source for each mapping decision.
- Ship as a valid Pi Package installable via `pi install npm:@sherif-fanous/pi-catppuccin`.
- Include optional HTML export colors for `/export` output.

**Non-Goals:**

- Custom accent color selection (e.g., user-configurable accent from the 14 accent colors) — all flavors use Mauve as the primary accent.
- Extension code — this package contains only static theme JSON files.
- Supporting palette versions other than v1.7.1.

## Decisions

### 1. Color Token Mapping

Every Pi theme token is mapped to a Catppuccin palette color below. The `vars` block in each theme JSON defines named palette aliases, and the `colors` block references those vars. This table documents the mapping for **all flavors** (same palette-name mapping; hex values differ per flavor).

#### Core UI (11 tokens)

| Pi Token       | Catppuccin Color | Source                                                                                          |
| -------------- | ---------------- | ----------------------------------------------------------------------------------------------- |
| `accent`       | Mauve            | Source: Style Guide:Code Editors:Language Defaults:Keyword — Mauve is the chosen primary accent |
| `border`       | Overlay 1        | Source: Style Guide:Background Colors:Overlays — one step more prominent than Inactive Border   |
| `borderAccent` | Mauve            | Source: Consistent with `accent` choice                                                         |
| `borderMuted`  | Overlay 0        | Source: Style Guide:Terminals:Inactive Border                                                   |
| `success`      | Green            | Source: Style Guide:Typography:Success                                                          |
| `error`        | Red              | Source: Style Guide:Typography:Errors                                                           |
| `warning`      | Yellow           | Source: Style Guide:Typography:Warnings                                                         |
| `muted`        | Overlay 1        | Source: Style Guide:Typography:Subtle                                                           |
| `dim`          | Overlay 0        | Source: Style Guide:Background Colors:Overlays — Overlay 0 as least prominent overlay           |
| `text`         | Text             | Source: Style Guide:Typography:Body Copy                                                        |
| `thinkingText` | Subtext 0        | Source: Style Guide:Typography:Sub-Headlines, Labels                                            |

#### Backgrounds & Content (11 tokens)

| Pi Token             | Catppuccin Color | Source                                                                                                     |
| -------------------- | ---------------- | ---------------------------------------------------------------------------------------------------------- |
| `selectedBg`         | Overlay 2        | Source: Style Guide:Typography:Selection Background — Overlay 2 (full opacity, no alpha blend)             |
| `userMessageBg`      | Surface 0        | Source: Style Guide:Background Colors:Surface Elements — Surface 0 distinguishes user content from base bg |
| `userMessageText`    | Text             | Source: Style Guide:Typography:Body Copy                                                                   |
| `customMessageBg`    | Surface 0        | Source: Style Guide:Background Colors:Surface Elements                                                     |
| `customMessageText`  | Text             | Source: Style Guide:Typography:Body Copy                                                                   |
| `customMessageLabel` | Mauve            | Source: Consistent with `accent` choice                                                                    |
| `toolPendingBg`      | Mantle           | Source: Style Guide:Background Colors:Secondary Panes — Mantle for secondary pane backgrounds              |
| `toolSuccessBg`      | Mantle           | Source: Style Guide:Background Colors:Secondary Panes — same bg, success indicated by border/title         |
| `toolErrorBg`        | Mantle           | Source: Style Guide:Background Colors:Secondary Panes                                                      |
| `toolTitle`          | Mauve            | Source: Consistent with `accent` choice                                                                    |
| `toolOutput`         | Subtext 1        | Source: Style Guide:Typography:Sub-Headlines, Labels — slightly dimmer than body for secondary output      |

#### Markdown (10 tokens)

| Pi Token            | Catppuccin Color | Source                                                                                                                   |
| ------------------- | ---------------- | ------------------------------------------------------------------------------------------------------------------------ |
| `mdHeading`         | Red              | Source: VS Code Catppuccin:`heading.1.markdown` — Red is the H1 color; Pi has a single heading token, so H1 is canonical |
| `mdLink`            | Lavender         | Source: VS Code Catppuccin:`string.other.link.title.markdown`                                                            |
| `mdLinkUrl`         | Blue             | Source: VS Code Catppuccin:`punctuation.definition.link`, `markup.underline.link`                                        |
| `mdCode`            | Green            | Source: VS Code Catppuccin:`markup.inline.raw.string.markdown`                                                           |
| `mdCodeBlock`       | Text             | Source: Style Guide:Typography:Body Copy — code block content uses body text color                                       |
| `mdCodeBlockBorder` | Overlay 2        | Source: VS Code Catppuccin:`markup.fenced_code.block punctuation.definition`                                             |
| `mdQuote`           | Pink             | Source: VS Code Catppuccin:`markup.quote`                                                                                |
| `mdQuoteBorder`     | Pink             | Source: VS Code Catppuccin:`punctuation.definition.quote.begin` (same scope as quote text)                               |
| `mdHr`              | Teal             | Source: VS Code Catppuccin:`meta.separator.markdown`                                                                     |
| `mdListBullet`      | Teal             | Source: VS Code Catppuccin:`punctuation.definition.list.begin.markdown`                                                  |

#### Tool Diffs (3 tokens)

| Pi Token          | Catppuccin Color | Source                                                                                           |
| ----------------- | ---------------- | ------------------------------------------------------------------------------------------------ |
| `toolDiffAdded`   | Green            | Source: Style Guide:Diff & Merge:Inserted                                                        |
| `toolDiffRemoved` | Red              | Source: Style Guide:Diff & Merge:Removed                                                         |
| `toolDiffContext` | Overlay 2        | Source: Style Guide:Diff & Merge:Index Metadata — context lines are supplementary, not the focus |

#### Syntax Highlighting (9 tokens)

| Pi Token            | Catppuccin Color | Source                                                                                              |
| ------------------- | ---------------- | --------------------------------------------------------------------------------------------------- |
| `syntaxComment`     | Overlay 2        | Source: Style Guide:Code Editors:Language Defaults:Comments                                         |
| `syntaxKeyword`     | Mauve            | Source: Style Guide:Code Editors:Language Defaults:Keyword                                          |
| `syntaxFunction`    | Blue             | Source: Style Guide:Code Editors:Language Defaults:Methods, Functions                               |
| `syntaxVariable`    | Maroon           | Source: Style Guide:Code Editors:Language Defaults:Parameters (closest match for general variables) |
| `syntaxString`      | Green            | Source: Style Guide:Code Editors:Language Defaults:Strings                                          |
| `syntaxNumber`      | Peach            | Source: Style Guide:Code Editors:Language Defaults:Constants, Numbers                               |
| `syntaxType`        | Yellow           | Source: Style Guide:Code Editors:Language Defaults:Classes, Interfaces, Types                       |
| `syntaxOperator`    | Sky              | Source: Style Guide:Code Editors:Language Defaults:Operators                                        |
| `syntaxPunctuation` | Overlay 2        | Source: Style Guide:Code Editors:Language Defaults:Braces, Delimiters                               |

#### Thinking Level Borders (6 tokens)

These form a visual hierarchy from subtle to prominent, mapped to the Catppuccin rainbow highlights in reverse order (warm = intense):

| Pi Token          | Catppuccin Color | Source                                                                               |
| ----------------- | ---------------- | ------------------------------------------------------------------------------------ |
| `thinkingOff`     | Surface 2        | Source: Style Guide:Background Colors:Surface Elements — most subtle, visually "off" |
| `thinkingMinimal` | Sapphire         | Source: Style Guide:Rainbow Highlights:Color #5 (reversed) — coolest, least intense  |
| `thinkingLow`     | Green            | Source: Style Guide:Rainbow Highlights:Color #4 (reversed)                           |
| `thinkingMedium`  | Yellow           | Source: Style Guide:Rainbow Highlights:Color #3 (reversed)                           |
| `thinkingHigh`    | Peach            | Source: Style Guide:Rainbow Highlights:Color #2 (reversed) — warm, high intensity    |
| `thinkingXhigh`   | Red              | Source: Style Guide:Rainbow Highlights:Color #1 (reversed) — maximum urgency         |

#### Bash Mode (1 token)

| Pi Token   | Catppuccin Color | Source                                                                                                                  |
| ---------- | ---------------- | ----------------------------------------------------------------------------------------------------------------------- |
| `bashMode` | Peach            | Source: Style Guide:Code Editors:General:Warnings — Peach as a warning-adjacent, attention-grabbing color for bash mode |

#### HTML Export (optional)

| Export Token | Catppuccin Color | Source                                                                       |
| ------------ | ---------------- | ---------------------------------------------------------------------------- |
| `pageBg`     | Crust            | Source: Style Guide:Background Colors:Secondary Panes — outermost background |
| `cardBg`     | Base             | Source: Style Guide:Background Colors:Background Pane                        |
| `infoBg`     | Surface 0        | Source: Style Guide:Background Colors:Surface Elements                       |

### 2. Exact Hex Values Per Flavor

Values sourced from [Catppuccin palette v1.7.1](https://github.com/catppuccin/palette/blob/main/palette.json):

| Palette Name | Latte     | Frappé    | Macchiato | Mocha     |
| ------------ | --------- | --------- | --------- | --------- |
| Rosewater    | `#dc8a78` | `#f2d5cf` | `#f4dbd6` | `#f5e0dc` |
| Flamingo     | `#dd7878` | `#eebebe` | `#f0c6c6` | `#f2cdcd` |
| Pink         | `#ea76cb` | `#f4b8e4` | `#f5bde6` | `#f5c2e7` |
| Mauve        | `#8839ef` | `#ca9ee6` | `#c6a0f6` | `#cba6f7` |
| Red          | `#d20f39` | `#e78284` | `#ed8796` | `#f38ba8` |
| Maroon       | `#e64553` | `#ea999c` | `#ee99a0` | `#eba0ac` |
| Peach        | `#fe640b` | `#ef9f76` | `#f5a97f` | `#fab387` |
| Yellow       | `#df8e1d` | `#e5c890` | `#eed49f` | `#f9e2af` |
| Green        | `#40a02b` | `#a6d189` | `#a6da95` | `#a6e3a1` |
| Teal         | `#179299` | `#81c8be` | `#8bd5ca` | `#94e2d5` |
| Sky          | `#04a5e5` | `#99d1db` | `#91d7e3` | `#89dceb` |
| Sapphire     | `#209fb5` | `#85c1dc` | `#7dc4e4` | `#74c7ec` |
| Blue         | `#1e66f5` | `#8caaee` | `#8aadf4` | `#89b4fa` |
| Lavender     | `#7287fd` | `#babbf1` | `#b7bdf8` | `#b4befe` |
| Text         | `#4c4f69` | `#c6d0f5` | `#cad3f5` | `#cdd6f4` |
| Subtext 1    | `#5c5f77` | `#b5bfe2` | `#b8c0e0` | `#bac2de` |
| Subtext 0    | `#6c6f85` | `#a5adce` | `#a5adcb` | `#a6adc8` |
| Overlay 2    | `#7c7f93` | `#949cbb` | `#939ab7` | `#9399b2` |
| Overlay 1    | `#8c8fa1` | `#838ba7` | `#8087a2` | `#7f849c` |
| Overlay 0    | `#9ca0b0` | `#737994` | `#6e738d` | `#6c7086` |
| Surface 2    | `#acb0be` | `#626880` | `#5b6078` | `#585b70` |
| Surface 1    | `#bcc0cc` | `#51576d` | `#494d64` | `#45475a` |
| Surface 0    | `#ccd0da` | `#414559` | `#363a4f` | `#313244` |
| Base         | `#eff1f5` | `#303446` | `#24273a` | `#1e1e2e` |
| Mantle       | `#e6e9ef` | `#292c3c` | `#1e2030` | `#181825` |
| Crust        | `#dce0e8` | `#232634` | `#181926` | `#11111b` |

### 3. Package Structure

```shell
pi-catppuccin/
├── themes/
│   ├── catppuccin-latte.json
│   ├── catppuccin-frappe.json
│   ├── catppuccin-macchiato.json
│   └── catppuccin-mocha.json
├── package.json
├── README.md
├── LICENSE
├── CHANGELOG.md
├── .gitignore
└── .npmignore
```

- `package.json` declares `pi.themes: ["./themes"]` for automatic discovery.
- Theme file naming: `catppuccin-<flavor>.json` (lowercase, hyphenated).
- The `name` field inside each theme JSON uses the format `catppuccin-<flavor>` (e.g., `catppuccin-mocha`).

### 4. Vars Strategy

Each theme JSON defines a `vars` block with all 26 palette colors as named variables. The `colors` block then references these var names exclusively. This:

- Makes the mapping self-documenting
- Allows quick visual verification against the palette
- Keeps the `colors` block readable

## Risks / Trade-offs

- **[Single heading color]** → Pi has one `mdHeading` token but Catppuccin VS Code uses six distinct heading colors (rainbow: Red → Peach → Yellow → Green → Sapphire → Lavender). We use Red (H1) since Pi only supports a single color. **Mitigation**: This is a Pi limitation, not a theme issue; no action needed.
- **[Uniform tool backgrounds]** → Using Mantle for all three tool states (pending/success/error) means tool state is communicated through title/border color rather than background. This follows the Catppuccin ethos of subtle backgrounds. **Mitigation**: The `toolTitle` (Mauve) and status indicators provide sufficient differentiation.
