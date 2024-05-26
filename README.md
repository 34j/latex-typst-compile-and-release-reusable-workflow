# Reusable GitHub Actions Workflow for Building LaTeX/Typst Document and Creating Release

## Usage

```yaml
name: Build LaTeX/Typst document and Create Release

on:
  push:
    branches:
      - main
  pull_request:

jobs:
  release:
    uses: 34j/latex-typst-compile-and-release-reusable-workflow/.github/workflows/release.yml@main
    secrets:
      github_token: ${{ secrets.GITHUB_TOKEN }}
```
