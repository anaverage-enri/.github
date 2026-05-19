# .github

Contributor: **[Enri](https://github.com/anaverage-enri)**

A fallback `.github` repository that applies community health files and shared workflows across all of my repositories that don't define their own.

## Contents

```
.
├── .github/
│   └── workflows/
│       ├── labels.yml
│       ├── pr-size.yml
│       └── sync-labels.yml
├── ISSUE_TEMPLATE/
│   ├── bug_report.yml
│   ├── config.yml
│   └── feature_request.yml
├── CODE_OF_CONDUCT.md
├── CODEOWNERS
├── labeler.yml
├── LICENSE
├── PULL_REQUEST_TEMPLATE.md
└── README.md
```

## Workflows

| Workflow | Description |
|---|---|
| `labels.yml` | Syncs labels to all repositories |
| `pr-size.yml` | Automatically labels PRs by size |
| `sync-labels.yml` | Pushes the label manifest to downstream repos |

## Usage in consumer repos

Add thin callers in each consumer repo under `.github/workflows/`.

**PR Labels** — `.github/workflows/labels.yml`
```yaml
name: PR Labels

on:
  pull_request:
    types:
      - opened
      - synchronize
      - reopened

jobs:
  labels:
    uses: anaverage-enri/.github/.github/workflows/labels.yml@main
```

**PR Size** — `.github/workflows/pr-size.yml`
```yaml
name: PR Size

on:
  pull_request:
    types:
      - opened
      - synchronize
      - reopened

jobs:
  size:
    uses: anaverage-enri/.github/.github/workflows/pr-size.yml@main
```

**Sync Labels** — `.github/workflows/sync-labels.yml`
```yaml
name: Sync Labels

on:
  workflow_dispatch:

jobs:
  sync:
    uses: anaverage-enri/.github/.github/workflows/sync-labels.yml@main
    # Optionally:
    # with:
    #   delete-other-labels: true
```

---

Any suggestion or contribution is welcome.
