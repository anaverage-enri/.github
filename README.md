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

---

Any suggestion or contribution is welcome.
