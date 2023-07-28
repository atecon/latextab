# Introduction

This package creates Latex code representing a gretl matrix as a Latex table.

Please report bugs or comments on the gretl mailing list, write to
atecon@posteo.de or report an issue on github
(https://github.com/atecon/latextab).

You may also want to check out the `mat2latex()` function from the "extra"
addon which produces a string containing the representation of a matrix as a
Latex tabular environment.

# Public function

```
function string latextab(const matrix mat, const bundle params[null])
```

Create the Latex-code for writing a matrix (optionally with labels) as a
Latex-table.

**Note**: When the boolean switch `asdoc` is set to `FALSE` (see below), one
needs to load both the `threeparttable` and `booktabs` packages when compiling
the Latex document. So please add the following lines to your document:

```
\usepackage{booktabs}
\usepackage{threeparttable}
```


## Parameters

- `mat`:     `matrix`, Matrix to be written as a table. The matrix may have
             both row and column labels attached, respectively.
- `params`:  `bundle`, Additional parameters to tweak the table

The bundle `params` includes the following parameters which can be adapted by
the user:

- `bold_clabels`: bool, Switch to make bold column labels (default: TRUE).
- `bold_rlabels`: `bool`, Switch to make bold row labels (default: TRUE).
- `caption`: `string`, Caption (title) of the table.
- `clabels`: `strings`, Array of column labels (optional).
   Must equal the number of columns, `c`, of `mat` if no row-labels are passed.
   Otherwise, `c+1` columns labels must be passed.
- `digits`, `matrix`, Vector holding the number of digits for each column
   (default: 3 digits for each column).
- `enforce_decpoint`: `bool`, Enforce writing decimal points (default:
   TRUE).
- `filename`: `string`, Full path of the tex-code being stored (optional).
- `fontsize`: `string`, Set the font-size of the table (default:
  `\normalsize`).
- `label`: `string`, Label of the tex-table.
- `note`: `string`, Add a note below the table.
- `position`, `string`, Position the table in the tex-documents (default:
  `htbp`)
- `rlabels`: `strings`, Array of row labels (optional). Must equal the
   number of rows of `mat`.
- `asdoc`: `bool`, Switch to add the document headers such that the
   tex-file can be compiled if set to TRUE (=1) (FALSE (=0) as default).

## Returns

A string of the Latex-code is returned. Per default, the returned tex-file is
only a snippet which can be included into an existing Latex document.
Optionally, the tex file can be stored as a separate Tex document which can be
compiled.


# Changelog
* **v1.1 (July 2023)**
    * Bugfix: In case no row-labels were provided this provoked an error before.

* **v1.0 (April 2023)**
    * Full refactoring incl. a new user-interface and some parameter renaming
    * Add unit-tests

* **v0.3 (February 2023)**
    * Update help text
    * Add new switch "todoc"
    * Fix typos

* **v0.22 (May 2017)**
    * changed `outfile @path --write --quiet` to `outfile "@path" --write
--quiet`
    to allow for white-spaces in path

* **v0.21 (April 2016)**
   * Add font-size option

* **v0.2 (Dec. 2015)**
    * Add the possibility to determine the number of decimal places
    * Automatic detection NA values (these are ignored)
