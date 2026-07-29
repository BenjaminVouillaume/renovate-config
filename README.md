# Renovate Configuration

Shared Renovate presets to keep my projects up to date. Modular: extend the
`default` base, then add the mixins the repository needs.

## Usage

Add a `renovate.json` (or `.github/renovate.json`) to the consuming repository
and compose the presets:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": [
    "github>BenjaminVouillaume/renovate-config",
    "github>BenjaminVouillaume/renovate-config:github-actions",
    "github>BenjaminVouillaume/renovate-config:terraform"
  ]
}
```

## Presets

### `default` — base preset (always include it)

- Extends `config:best-practices` (dependency dashboard, GitHub Actions pinned to digests, config migration, ...)
- Runs every 2 weeks (Europe/Paris timezone)
- Enables the `pre-commit` manager (disabled in Renovate by default) and groups/automerges pre-commit updates (`minor`/`patch`/`pin`/`digest`; majors get individual PRs)

### `github-actions`

- Groups and automerges GitHub Actions updates (`minor`/`patch`/`pin`/`digest`; majors get individual PRs)

### `terraform`

- Groups and automerges Terraform updates (`terraform`, `terraform-version`, `tflint-plugin` managers; `minor`/`patch`/`pin`/`digest` only)
