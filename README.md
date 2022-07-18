# PRL-Paper-Template
A basic template for a PRL paper

## Getting Started

First you will need a TeX distribution on your system. This will depend on your operating system, but on Windows you can install [MiKTeX](https://miktex.org/). This distribution may also work on other operating systems. Once installed, you must install the `revtex` package. 

In Windows, search for "MiKTeX Console" and open this. Go to the "Packages" tab on the left hand side, and then search for `revtex`. There should be three options. Choose the most recent `revtex` package, which should be last updated 2020 or beyond. Right-click the option and install that package. I would also recommend installing `latexmk` via the same method. Next, go to Settings -> Package Installation -> Choose either "Always" or "Ask Me" for automatically downloading packages.

## Compiling

Go to the later section on VS Code for how to use an IDE to write your paper. This makes the process simpler.

If you prefer working with the console, and have installed `latexmk`, one can simply run in the console (in the root folder of this repository):
```bash
latexmk main.tex -pdf
```
This will compile to `main.pdf`. If this command does not work, you need to add MiKTeX to your path, which should be easy enough with a quick google search.

## GitHub

Try not to commit generated files. This includes `main.pdf`. If you want to share a current version of the `pdf`, create a release in GitHub, and upload a copy of `main.pdf` as a binary, and give it a tag. This will allow others to access the `pdf` without compiling the code, and will avoid all merge conflicts between users.

As a generally accepted practice, create an issue with the work you want to do, then create a branch from this issue and assign it to yourself, so that others can see what you are working on. Once finished, create a pull request to merge into main.

## Notes

- References are written in BibTeX format in `references.bib`.
- All figures are stored under the `figures/` subdirectory
- All sections are written in their own file, under the `sections/` directory
- Many packages that may not be needed are imported, and many can be removed.
- Abstract is written in a separate file - `abstract.tex`.
- Use `\input` instead of `\include` in `main.tex` for additional sections, as `\include` creates a new page.

## Tips for using VS Code

VS Code is a good choice for writing LaTeX, as it is compatible with Git and GitHub for sharing the source code with other contributors. The extensions `LaTeXWorkshop` by James Yu and `LTeX` by Julian Valentin provide excellent support for writing LaTeX, much like Overleaf. The following VS Code settings (stored in `.vscode/settings.json` - create if not found, but do not commit!) is an example.:

```json
{
    "latex-workshop.latex.autoBuild.run": "never",
    "editor.wordWrap": "on",
    "ltex.language": "en-GB"
}
```

### Example Code Snippets

Create a file in `.vscode/snippets.code-snippets`:

```json
{
    "Equation": {
        "prefix": ["\\beq", "\\equation"],
        "body": [
            "\\begin{equation}",
            "\t\\$1",
            "\\end{equation}",
			"$0"
        ],
        "description": "A standard template for an equation snippet in LaTeX."
    },
    "Figure": {
        "prefix": ["\\figure", "\\fig"],
        "body": [
            "\\begin{figure}",
            "\t\\centering",
            "\t\\includegraphics[width=\\singlefigure]{figures/$1}",
            "\t\\caption{\\label{fig:$2} $3}",
            "\\end{figure}",
            "$0"
        ],
        "description": "A standard template for a single column figure in LaTeX."
    }
}
```
