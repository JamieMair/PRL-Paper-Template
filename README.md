# PRL-Paper-Template
A basic template for a PRL paper

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
