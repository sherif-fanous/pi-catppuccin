## Context

The repository ships four Pi theme JSON files, one for each Catppuccin flavor. Each file already defines a complete Catppuccin palette in `vars` and routes all interactive UI color tokens through those names. The optional `export` section still uses duplicated hex literals for `pageBg`, `cardBg`, and `infoBg`, reflecting an older Pi limitation.

Recent inspection of the installed Pi source shows that `getThemeExportColors()` resolves export values through `resolveVarRefs(themeJson.vars)`, and the export schema uses the same `ColorValueSchema` as the main color tokens. That means the runtime now supports palette variable references in `export`.

## Goals / Non-Goals

**Goals:**

- Remove duplicated hex literals from the `export` sections of all four themes.
- Express export colors in the same var-based style used elsewhere in each theme.
- Preserve the currently resolved HTML export colors exactly.
- Record the behavioral requirement in OpenSpec so future edits keep using palette vars.

**Non-Goals:**

- Changing any palette hex values.
- Adjusting any `colors` token mappings.
- Altering theme names, package metadata, or README content.
- Adding compatibility workarounds for older Pi versions beyond the currently supported runtime behavior.

## Decisions

### Use var references in `export`

The `export` section will use named vars instead of hex literals:

- `pageBg` → `crust`
- `cardBg` → `base`
- `infoBg` → `surface_0`

This keeps the export section semantically tied to the same palette source of truth as the rest of the theme.

**Alternatives considered:**

- Keep raw hex values for maximum doc alignment. Rejected because it preserves duplication and no longer reflects actual Pi behavior.
- Remove the `export` section entirely and rely on Pi's derived export colors. Rejected because the project already defines explicit export output colors and wants to preserve them intentionally.

### Treat this as a spec change, not just a file edit

The current `theme-definitions` spec requires exact export hex values. Since the new representation changes how the theme files should be authored, the requirement should be updated to express var-based export entries while still preserving the same resolved color meaning.

**Alternatives considered:**

- Leave the spec unchanged and only update the files. Rejected because the spec would then contradict the desired source format.

## Risks / Trade-offs

- **Pi documentation still shows hex examples** → Mitigation: rely on verified runtime source behavior and record that rationale in change artifacts.
- **Users on older Pi builds might not resolve vars in `export`** → Mitigation: keep the change scoped to the currently observed Pi behavior and verify whether the project wants to support older versions before implementation.
- **Spec wording could become too implementation-specific** → Mitigation: phrase requirements in terms of required var references plus preserved resolved colors.
