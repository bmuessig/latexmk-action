# latexmk-action

Adapted for personal use from the original at <https://github.com/hspaans/latexmk-action>.

## Usage

This GitHub Action run latexmk to convert a LaTeX file into a PDF.

## Parameters

Following parameters can be used as `step.with` keys:

| Name       | Type   | Default    | Description                          |
| ---------- | ------ | ---------- | ------------------------------------ |
| `format`   | String | `pdf`      | Output format for the LaTeX filename |
| `filename` | String | `main.tex` | Source LaTeX filename to process     |
| `options`  | String |            | Additional options for latexmk       |

## Example

Example workflow to generate a PDF document from a LaTeX file:

```yaml
---
name: CI

on: [push]

jobs:
  build-test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v2

      - name: Generate PDF document
        uses: bmuessig/latexmk-action@v2.1.0
        with:
          format: pdf
          filename: article.tex
          options: -shell-escape
```

Example workflow to generate a PDF document from a LaTeX file `article.tex` with a configuration file `.latexmkrc`:

```yaml
---
name: CI

on: [push]

jobs:
  build-test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v2

      - name: Generate PDF document
        uses: bmuessig/latexmk-action@v2.1.0
        with:
          filename: article.tex
```

## Limitation

This action is only available for Linux [virtual environments](https://help.github.com/en/articles/virtual-environments-for-github-actions#supported-virtual-environments-and-hardware-resources).
