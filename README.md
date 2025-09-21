# LaTeX Template for Theses

An easy-to-use, modular LaTeX template for seminar papers, bachelor and master theses.

[![View PDF](https://img.shields.io/badge/View-Thesis_Template-red?style=for-the-badge&logo=readdotcv&logoColor=red)](Thesis-Template.pdf)

## Highlights

- Modular structure: separate files for frontmatter, chapters, configuration, and backmatter.
- Bibliography support with BibLaTeX and Biber.
- Support for figures, tables, algorithms/pseudocode, code listings, abbreviations/glossaries, and appendices.
- A Makefile for an easy build workflow.
- VS Code configuration (extensions and settings) for building PDF, formatting, linting, and spell checking

## Project Structure

```
├── Thesis-Template.tex      # Main entry file (includes config and content)
├── makefile                 # Convenience wrapper for build steps
│
├── config/                  # Configuration files
│   ├── packages.tex         # Package imports
│   ├── settings.tex         # Settings and styling
│   ├── abbreviations.tex    # Glossary/abbreviations definitions
│   └── literature.bib       # BibLaTeX bibliography file
│
├── frontmatter/             # Modular front matter
│   ├── titlepage.tex
│   ├── abstract.tex
│   ├── acknowledgments.tex
│   └── confidentiality.tex
│
├── chapters/                # Main content chapters
│   ├── 01_introduction.tex
│   ├── 02_background.tex
│   ├── ...
│   └── 06_conclusion.tex
│
├── backmatter/              # Modular back matter
│   ├── appendix.tex
│   └── declaration.tex
│
├── figures/                 # Images, logos, and other assets
│
├── .vscode/                 # VS Code configuration for consistent editing
│   ├── extensions.json      # Recommended extensions for LaTeX development
│   └── settings.json        # Editor settings (e.g., formatting, linting)
│
└── .github/workflows/       # GitHub Actions for CI/CD
    └── build-pdf.yml        # Workflow to automatically build the PDF
```

When adding new TeX files, include them in `Thesis-Template.tex` using `\input{path/to/file.tex}`.

## Usage Examples

- See the example content in `chapters/` for usage examples, including how to add and reference figures, tables, algorithms, code listings, and other common elements.
- Define bibliographic entries in `config/literature.bib`.
- Define abbreviations in `config/abbreviations.tex`.

## Local Setup

### Requirements

For the local setup, Linux (Debian/Ubuntu) is recommended. You can install all necessary packages with:

```
sudo apt-get install -y make texlive texlive-latex-extra texlive-extra-utils texlive-science biber chktex
```

This command installs:

- TeX Live: LaTeX distribution
- Biber: Bibliography handling with BibLaTeX
- make: Automates the build process
- latexindent: Formats LaTeX source code nicely
- chktex: Checks for typographic and other LaTeX issues

Visual Studio Code (VS Code) is recommended as the editor, as all necessary extensions and settings for formatting, linting, and spell checking are already pre-configured in the `.vscode` folder.

### Build PDF

First, the repository must be downloaded or cloned. Then, run the following command in the project's root directory to generate the final PDF:

```
make
```

This will execute the following sequence:

1. `pdflatex -synctex=1 -interaction=nonstopmode -file-line-error Thesis-Template.tex`
2. `biber Thesis-Template`
3. `makeglossaries Thesis-Template`
4. `pdflatex -synctex=1 -interaction=nonstopmode Thesis-Template.tex`
5. `pdflatex -synctex=1 -interaction=nonstopmode Thesis-Template.tex`
