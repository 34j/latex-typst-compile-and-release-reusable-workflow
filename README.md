# Reusable GitHub Actions Workflow for Building LaTeX/Typst Document and Creating Release

## Usage

1. Set `Settings/Actions/General/Workflow Permissions` to `Read and write permissions`
2. `.github/workflows/release.yaml`

```yaml
name: Build LaTeX/Typst document and Create Release

on:
  push:
    branches:
      - main
  pull_request:

jobs:
  release:
    uses: 34j/latex-typst-compile-and-release-reusable-workflow/.github/workflows/release.yaml@main
    secrets:
      gh_pat: ${{ secrets.GITHUB_TOKEN }}
```

## Advanced Usage

```yaml
name: Build LaTeX/Typst document and Create Release

on:
  push:
    branches:
      - main
  pull_request:

jobs:
  release:
    uses: 34j/latex-typst-compile-and-release-reusable-workflow/.github/workflows/release.yaml@main
    with:
      cluttex_parallel: true
      cluttex: false
      latexmk: false
      typst: true
      upload_artifact: true
      upload_release: ${{ github.event_name == 'push' }}
    secrets:
      gh_pat: ${{ secrets.GITHUB_TOKEN }}
```
