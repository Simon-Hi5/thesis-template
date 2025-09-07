# LaTeX Template for Theses

An easy-to-use, modular LaTeX template for seminar papers, bachelor and master theses.

[![View PDF](https://img.shields.io/badge/View-Thesis_Template-red?style=for-the-badge&logo=readdotcv&logoColor=red)](Thesis-Template.pdf)

## Highlights

- Modular structure: separate files for frontmatter, chapters, configuration and backmatter.
- Pre-configured bibliography support with BibLaTeX and Biber.
- Support for figures, tables, algorithms/pseudocode, code listings, abbreviations/glossaries and appendices.
- A Makefile for an easy build workflow.

## Project Structure

```
├── Thesis-Template.tex      # Main entry file (includes config and content)
├── makefile                 # Convenience wrapper for build steps
│
├── config/                  # Configuration files
│   ├── packages.tex         # Package imports and general LaTeX settings
│   ├── settings.tex         # Document-specific settings (title, author, etc.)
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
├── backmatter/              # Appendices and declarations
│   ├── appendix.tex
│   └── declaration.tex
│
└── figures/                 # Images, logos, and other assets
```

When adding new TeX files, include them in `Thesis-Template.tex` using `\input{path/to/file.tex}`.

## Usage Examples

- See the example content in `chapters/` for usage examples, including how to add and reference figures, tables, algorithms, code listings, and other common elements.
- Define bibliographic entries in `config/literature.bib`.
- Define abbreviations in `config/abbreviations.tex`.

## Local Setup

### Requirements

- A TeX distribution (TeX Live recommended).
- Biber (for bibliography processing).
- make (optional, the Makefile wraps the build commands).

On Linux (Debian/Ubuntu) you can install the basics with:

`sudo apt install texlive-extra biber make`

### Build PDF

1. `pdflatex -synctex=1 -interaction=nonstopmode Thesis-Template.tex`
2. `biber Thesis-Template`
3. `makeglossaries Thesis-Template`
4. `pdflatex -synctex=1 -interaction=nonstopmode Thesis-Template.tex`
5. `pdflatex -synctex=1 -interaction=nonstopmode Thesis-Template.tex`

Or simply run:

`make`
