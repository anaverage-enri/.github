# .github

Contributor: **[Enri](https://github.com/anaverage-enri)**

A fallback `.github` repository that applies community health files and shared workflows across all of my repositories that don't define their own.

## Contents

```
.
├── .github/
│   └── workflows/
│       ├── label-sync.yml
│       ├── path-labeler.yml
│       └── size-labeler.yml
├── ISSUE_TEMPLATE/
│   ├── bug_report.yml
│   ├── config.yml
│   └── feature_request.yml
├── CODE_OF_CONDUCT.md
├── CODEOWNERS
├── .github-labels.yml
├── path-labels.yml
├── LICENSE
├── PULL_REQUEST_TEMPLATE.md
└── README.md
```

## Workflows

| Workflow | Description |
|---|---|
| `path-labeler.yml` | Labels PRs by changed file paths |
| `size-labeler.yml` | Labels PRs by size (XS–XXL) |
| `label-sync.yml` | Syncs repository label definitions from the central `.github-labels.yml` manifest |

## Usage in consumer repos

Add thin callers in each consumer repo under `.github/workflows/`.

**Label PR by Changed Paths** — `.github/workflows/path-labeler.yml`
```yaml
name: Label PR by Changed Paths

on:
  pull_request:
    types:
      - opened
      - synchronize
      - reopened

jobs:
  labels:
    uses: anaverage-enri/.github/.github/workflows/path-labeler.yml@main
```

**Label PR by Size** — `.github/workflows/size-labeler.yml`
```yaml
name: Label PR by Size

on:
  pull_request:
    types:
      - opened
      - synchronize
      - reopened

jobs:
  size:
    uses: anaverage-enri/.github/.github/workflows/size-labeler.yml@main
```

**Sync Repository Label Definitions** — `.github/workflows/label-sync.yml`
```yaml
name: Sync Repository Label Definitions

on:
  workflow_dispatch:

permissions:
  contents: read
  issues: write

jobs:
  sync:
    uses: anaverage-enri/.github/.github/workflows/label-sync.yml@main
    # Optionally:
    # with:
    #   delete-other-labels: true
```

---

Any suggestion or contribution is welcome.
