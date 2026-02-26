# AGENTS.md

## Cursor Cloud specific instructions

This is a **data-only repository** — there is no backend, frontend, or runnable service. The repo is an open merchant registry (`merchants.json`) validated against a JSON Schema (`schema.json`).

### Validation (lint/test equivalent)

The full CI validation suite (see `.github/workflows/validate.yml`) can be run locally:

```bash
# JSON Schema validation
ajv validate -s schema.json -d merchants.json --verbose

# Duplicate domain check (should produce no output)
jq -r '.merchants[].domain' merchants.json | sort | uniq -d

# Domain format check — no protocol prefix allowed (should produce no output)
jq -r '.merchants[].domain' merchants.json | grep -E '^https?://' || true
```

**Required tools:** `ajv-cli`, `ajv-formats` (installed globally via npm), and `jq`.

### Key gotchas

- There is no `package.json` or lockfile in this repo; `ajv-cli` and `ajv-formats` are installed globally (`npm install -g ajv-cli ajv-formats`).
- The CI workflow uses Node.js 20, but any recent Node.js version works for `ajv-cli`.
- `merchants.json` entries must conform to `schema.json` (JSON Schema draft-07). Each merchant needs `domain`, `name`, `category`, and `protocols` fields.
- Domains must **not** include a protocol prefix (`https://`) or trailing slash.
