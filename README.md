# tkz-euclide — Euclidean Geometry with TikZ
Release 5.14c-mod1 — 2026/11/16

Personal modified release based on upstream 5.14c. See Changelog.md for fork changes.
The bundled PDF is the rebuilt manual, including the modified interfaces documented in doc/latex.

## Description

`tkz-euclide` is a LaTeX package for drawing two-dimensional Euclidean
geometric figures. It uses a Cartesian orthonormal coordinate system
(unit = 1 cm) and provides tools to define points and manipulate them.
The goal is to reproduce, step by step, constructions as they would be
done by hand, in the most natural way possible.

Recent updates:
- **`lua` option**: most calculations can now be performed using Lua.
- **`mini` option**: when `tkz-euclide` is used together with
  [`tkz-elements`](https://ctan.org/pkg/tkz-elements), this option lets
  `tkz-euclide` focus only on the drawings. Some macros, such as those in the `tkz-draw-eu-show.tex` file, still require the use of the complete package.

## License

This package is released under the
[LaTeX Project Public License](https://www.latex-project.org/lppl/),
version 1.3c or later.

## Requirements

`tkz-euclide` requires LaTeX with UTF-8 input and works with both
**pdfLaTeX** and **LuaLaTeX**. It depends on up-to-date versions of:

- [xfp](https://ctan.org/pkg/xfp)
- [tikz](https://ctan.org/pkg/tikz)

## Installation

The package is available on **TeX Live** and **MiKTeX**. Use your package
manager to install it.

For local testing, place the distribution files in the same directory as
your `.tex` file. For permanent installation, move the files into your
local `TEXMFHOME` or system `TDS` tree.

## Usage

If you also use `tkz-base`, load it before `tkz-euclide`. Shared commands
and configuration are always provided by `tkz-euclide`.

Add the following lines to your preamble:

```latex
\usepackage{tkz-euclide}

\begin{document}
\begin{tikzpicture}
  % your code here
\end{tikzpicture}
\end{document}
```


## Building the manual

Compile `doc/latex/TKZdoc-euclide-main.tex` with LuaLaTeX and MakeIndex.
In addition to the package dependencies, install `tkz-doc`, `tkz-base`,
`tkzexample`, `pgfornament`, `ulem`, `fourier-otf` (including Erewhon,
Erewhon Math and Fourier ornaments), TeX Gyre and Latin Modern fonts.
A complete TeX Live installation supplies these dependencies.

From the repository root, build outside the checkout:

```sh
repo="$PWD"
build="$(mktemp -d)"
cp -R doc/latex/. "$build/"
cd "$build"
export TEXINPUTS="$repo/latex//:${TEXINPUTS-}"
lualatex -interaction=nonstopmode -halt-on-error TKZdoc-euclide-main.tex
makeindex TKZdoc-euclide-main.idx
lualatex -interaction=nonstopmode -halt-on-error TKZdoc-euclide-main.tex
makeindex TKZdoc-euclide-main.idx
lualatex -interaction=nonstopmode -halt-on-error TKZdoc-euclide-main.tex
```

Rerun LuaLaTeX and MakeIndex if the log still requests updated references
or the index page numbers have changed.

## Author

Alain Matthes, 5 rue de Valence, Paris 75005, al (dot) ma (at) mac (dot) com
