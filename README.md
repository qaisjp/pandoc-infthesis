# pandoc-infthesis

Here's a template for writing your honours project in Markdown, but still using [the infthesis LaTeX template](https://www.inf.ed.ac.uk/teaching/courses/proj/Latex/index.html).

## Directory structure

- `chapters` folder contains your content. It's all joined together by alphabetical order, hence the numbers
- `includes` folder contains useful stuff to configure things
    - `includes/before-body.tex` contains your acknowledgments and declaration
    - `includes/header.tex` includes your degree, project kind and abstract
    - `includes/bibliography.yaml` is what it sounds like, but in YAML format.
    - `includes/metadata.yaml` configures pandoc and other pandoc filters, incl. the title and author

## Installing

**For LaTeX**

On macOS you need `brew cask install mactex` (3.8GB). On Linux... who knows.

You probably don't need the full thing, but that's what I have installed.

**Everything else**

On macOS you can just do: `brew install pandoc pandoc-citeproc pandoc-crossref`.

On Linux you can probably install `pandoc` and `pandoc-citeproc` from your package manager.
[`pandoc-crossref`] is harder to install, hard enough for me (or takes too long to install) to give up on adding continuous integration to this repo.

Pandoc uses Haskell, so you will need to install stuff. `pandoc-citeproc` is essential but you can survive without `pandoc-crossref`. You'll just lose a bunch of nifty features for referencing sections, figures, equations and tables.

[`pandoc-crossref`]:https://github.com/lierdakil/pandoc-crossref

## Usage

1. Read the entirety of this README file
1. Read all the files (even the Makefile!)
1. Run `make` and then you can just open `project.pdf`

## FAQ

**Does my bibliography need to be in YAML?**

[No, you can use any of the formats listed here.](https://pandoc.org/MANUAL.html#citations)
So that means `.bib`/`.bibtex` are supported. You just need to tweak this repo (the `Makefile`) to add support for it.

That link also provides a command for _automatically_ converting an existing `.bib(tex)` to a `.yaml` or `.json`.

**How do I configure pandoc / pandoc-citeproc / pandoc-crossref?**

There are links to documentation in `bibliography.yaml` and `metadata.yaml`. Recommended reading.

You can also just write LaTeX where you need to inside the markdown.
You'll notice I already do this a little for `\chapter{Some Chapter}`.

I'm not kidding when I say read the links to the documentation. There's some
really useful extensions here:

> Pandoc’s enhanced version of Markdown includes syntax for tables, definition lists, metadata blocks, footnotes, citations, math, and much more. See below under [Pandoc’s Markdown](https://pandoc.org/MANUAL.html#pandocs-markdown).

If you have existing stuff in LaTeX, just copy the content to a new `.tex` file, and use this command to convert it to Markdown: `pandoc old.tex -o new.md`

**How do I get numbered citations?**

[Footnotes work fine, read the docs](https://pandoc.org/MANUAL.html#footnotes). I can't get numbering to work for our endnotes, the bibliography, however. This ["How to use Pandoc to product a research paper"](https://opensource.com/article/18/9/pandoc-research-paper) article says that it will just output a number, but for some reason it doesn't actually do that. `¯\_(ツ)_/¯`.

## Caveats

* Markdown images are relative to the root of the repo, not relative to the markdown file. This will cause images to not show up correctly on GitHub or any other renderer. See [jgm/pandoc#3752](https://github.com/jgm/pandoc/issues/3752).
* And any other problems mentioned in the FAQ.

## License

The Unlicense, except `infthesis.cls` and `eushield.sty` which is probably owned by The University of Edinburgh. That basically means you can do whatever you like with it. It's public domain.
