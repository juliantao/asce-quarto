# asce-quarto

## Table of Contents

 * [About](#about)
 * [Guide](#guide)
    * [Fork and clone](#fork-and-clone)
    * [Editing](#editing)
       * [Publication type and other options](#publication-type-and-other-options)
       * [Title block](#title-block)
       * [Appendix](#appendix)
       * [Bibliography and references](#bibliography-and-references)
    * [Repo structure and organization](#repo-structure-and-organization)
 * [Caveats](#caveats)
 * [Todo](#todo)

# About

This is a hackish [`quarto`](https://quarto.org/) template for ASCE publications based on the [`ascelike-new` class](https://www.overleaf.com/latex/templates/template-for-preparing-your-submission-to-the-american-society-of-civil-engineers-asce/pbwcqsvndpty).

This template is intended to be used before the official `rticle`-like `quarto` template mechanism is released (see [here](https://quarto.org/docs/faq/rmarkdown.html#i-use-x-bookdown-blogdown-etc..-what-is-the-quarto-equivalent), [here](https://github.com/quarto-dev/quarto-cli/issues/170), and [here](https://github.com/quarto-dev/quarto-cli/discussions/983#discussioncomment-2823436)).

The majority of the `qmd` file was directly converted from `ascexmpl-new.tex` from the [overleaf template](https://www.overleaf.com/latex/templates/template-for-preparing-your-submission-to-the-american-society-of-civil-engineers-asce/pbwcqsvndpty) using [`pandoc`](https://pandoc.org/). 
The following tweaks are made:

* The tables are now prepared using the pipe style;
* Cross-referencing now follows the quarto syntax; 
* A figure from an embedded python code is included;
* An `pdf` figure is used to replace the original figure placeholder;
* The original `ascelike-new.bst` file is not included since the citation style is now handled using a [`CSL` file](https://www.zotero.org/styles/american-society-of-civil-engineers?source=1);
* The styles related to citation in the `ascelike-new.cls` are also commented out.

# Guide

## Making a copy

To use this template, [fork](https://github.com/juliantao/asce-quarto/fork), clone or click the [`Use this template`](https://github.com/juliantao/asce-quarto/generate) button. 

A more convenient way is to use [`github cli`](https://cli.github.com/)

```bash
gh repo create "new-repo-name" --private --clone -p "https://github.com/juliantao/asce-quarto"
```

  * `gh repo create "new-repo-name"` creates a new github repo with the name `new-repo-name` 
  * `--private` makes the github repo private before submission
  * `--clone` clones the remote repo to a local repo in the current directory and links the two
  * `-p "https://github.com/juliantao/asce-quarto"` uses the `asce-quarto` repo as a template

## Editing

### Publication type and other options

In the shared matadata `_quarto.yml`,
  * Set `classoption: [NewProceedings, letterpaper]` for conference paper
  * Set `classoption: [Journal, letterpaper]` for journal paper
  * by default, the rendered files will be in the `_output` folder, change as you wish

### Title block

* In the `yaml` header of the main `qmd` file, 
  * **do not** include the **title** field
  * ONLY include the **first author** for the `author` field

* Right after the `yaml` header in the main `qmd` and before the `# Abstract` section, include the remaining parts of the `title` block using raw `LaTex`:

```latex
\title{Template for Preparing Your Submission to the American Society Of Civil Engineers (ASCE)}

% do not redefine author one again

\author[2]{Author Two}
\author[3]{Author Three}

\affil[1]{First affiliation address, with corresponding author email. Email: author.one@email.com}
\affil[2]{Second affiliation address}
\affil[2]{Third affiliation address}

\maketitle
```

### Appendix

* Add `\appendix` before the appendix sections so that the section titles can be properly rendered. 
  When referencing an appendix section, use syntax `Appendix [-@sec-label]`, this will be rendered to something like `Appendix I`.

### Bibliography and references

* Update the `references.bib` file in the `./assets/` directory

* Add a section title for the references at the end of the main `qmd` file

```markdown
# References {-}

::: {.refs}
:::
```

## Repo structure and organization

It is suggested to have a meaningful structure of the directory. 
For example, this template has the following tree structure.
The `data` and `code` directories are empty but should be updated for your paper.

```
.
├── assets
│   ├── american-society-of-civil-engineers.csl
│   ├── ascelike-new.cls
│   └── references.bib
├── code
├── data
├── example-original.tex
├── example.qmd
├── example.tex
├── img
│   └── asce-logo.pdf
├── LICENSE
├── _output
│   ├── example_files
│   │   └── figure-pdf
│   │       └── fig-fill-between-output-1.pdf
│   └── example.pdf
├── _quarto.yml
└── README.md
```

# Caveats

* This template works only for `pdf` and `tex` format now. 
Although a word template file is also provided, the rendered docx file is not ideal.
Currently, the best way to generate a `docx` file with comparable layout is using Acrobat DC from Adobe to convert the generated pdf file directly to docx file.

* If you have an old `texlive` distribution, there may be a warning on option crash. Please update `texlive`. It is also recommended that you use the latest version of [Quarto](https://quarto.org/docs/get-started/).
* Alternatively, you can comment out the line `- \usepackage{newtxtext,newtxmath}` in `_quarto.yml`. 
The `lmodern` fonts will be used, which will look different from the official template.
But it is not a great deal...

# Todo

- [x] ~~figure out the numbering for appendix~~
- [x] ~~figure out a better way to cross-reference appendices~~
- [ ] also ensure `html` format can be rendered with the title block
- [ ] improve `docx` output format
