This is a hackish [`quarto`](https://quarto.org/) template for ASCE publications based on the [`ascelike-new` class](https://www.overleaf.com/latex/templates/template-for-preparing-your-submission-to-the-american-society-of-civil-engineers-asce/pbwcqsvndpty).

This template can be used before the official `rticle` like `quarto` template mechanism is released (see [here](https://quarto.org/docs/faq/rmarkdown.html#i-use-x-bookdown-blogdown-etc..-what-is-the-quarto-equivalent), [here](https://github.com/quarto-dev/quarto-cli/issues/170), and [here](https://github.com/quarto-dev/quarto-cli/discussions/983#discussioncomment-2823436).

To use this template, fork or click [`Use this template`](https://github.com/juliantao/asce-quarto/generate) button and then do the following:

* In the shared matadata `_quarto.yml`,
  * Set `classoption: [NewProceedings, letterpaper]` for conference paper
  * Set `classoption: [Journal, letterpaper]` for journal paper
  * by default, the rendered files will be in the `_output` folder, change as you wish

* Update the `references.bib` file in the `./assets/` directory

* In the `yaml` header of the main `qmd` file, 
  * **do not** include the **title** field
  * include the **first author** for the `author` field
  * set `format: pdf` for submission

* Before the `# Abstract` section, including the remaining parts of the `title` block using raw `LaTex`:

```latex
\title{Template for Preparing Your Submission to the American Society Of Civil Engineers (ASCE)}

% do note redefine author one again

\author[2]{Author Two}
\author[3]{Author Three}

\affil[1]{First affiliation address, with corresponding author email. Email: author.one@email.com}
\affil[2]{Second affiliation address}
\affil[2]{Third affiliation address}

\maketitle
```

Todo:

- [ ] also ensure `html` format can be rendered with the title block
- [ ] figure out the appendix numbering

  





  
