<p align="center">
  <img src="https://raw.githubusercontent.com/go-typeset/brand/main/png/color/256/go-typeset.png" alt="go-typeset" width="88" height="88">
</p>

# go-typeset

[![License](https://img.shields.io/badge/license-BSD--3--Clause-blue.svg)](https://github.com/go-typeset/linebreak/blob/main/LICENSE)
[![Pure Go](https://img.shields.io/badge/pure%20Go-CGO%3D0-00ADD8?logo=go&logoColor=white)](https://github.com/go-typeset)
[![Coverage](https://img.shields.io/badge/coverage-100%25-1a7f37)](https://github.com/go-typeset)

**The algorithms that place marks on a page** — pure Go, CGO=0, standard library
only. Typesetting, not typography: these libraries decide *where* text goes, not
what the letters look like.

They came out of the [go-tex](https://github.com/go-tex) engine, where they were
already written as self-contained algorithms with no reference to engine state.
Extracting them was a move, not a rewrite — and their public API carries **no TeX
vocabulary**, because a paragraph breaker is not a TeX component.

## Repositories

| Repo | What it is |
|------|------------|
| [**linebreak**](https://github.com/go-typeset/linebreak) | **Knuth–Plass** optimal line breaking: the box/glue/penalty model and the paragraph builder that made TeX's paragraphs what they are |
| [**hyphenation**](https://github.com/go-typeset/hyphenation) | **Liang's algorithm**, reading TeX's own pattern files |
| [**bidi**](https://github.com/go-typeset/bidi) | the **Unicode bidirectional algorithm** |

## Why these live together, and not elsewhere

`bidi` used to sit under [go-opentype](https://github.com/go-opentype). Measurement
settled the move: `shape` and `fonts` genuinely import `opentype`, while `bidi`
imports **nothing**. It was there by contagion, not by reasoning — and an anomaly
is not an argument.

Anything that lays out text — a PDF writer, an e-book renderer, a terminal
formatter, a widget toolkit — reuses these rather than reimplementing them.
