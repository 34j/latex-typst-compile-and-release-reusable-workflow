# Reusable GitHub Actions Workflow for Building LaTeX/Typst Document and Creating Release

## Features

- Support both LaTeX ([LaTeXmk][latexmk] or [Cluttex][cluttex]) and [Typst][typst]
- Install custom fonts from [Google Fonts][google-fonts]
- Comment the link to the Compiled PDF file in the Pull Request
- Automatically create a release with the compiled PDF file attached

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
      upload_release: true
      fonts: '"Roboto" "Noto Sans" "Noto Serif"' # Google Fonts
      runs-on: '["self-hosted", "linux"]' # use self-hosted runner
    secrets:
      gh_pat: ${{ secrets.GITHUB_TOKEN }}
```

[latexmk]: https://ctan.org/pkg/latexmk
[cluttex]: https://ctan.org/pkg/cluttex
[typst]: https://github.com/typst/typst
[google-fonts]: https://fonts.google.com/
