# adelaide-harvard-natbib-style

![Static Badge](https://img.shields.io/badge/Working_status-Under_development-pink?link=https%3A%2F%2Fgithub.com%2Fhxt-tg%2Fadelaide-harvard-natbib-style)
![Version Badge](https://img.shields.io/badge/Version-0.1.1-blue?link=https%3A%2F%2Fgithub.com%2Fhxt-tg%2Fadelaide-harvard-natbib-style)


A LaTeX natlib bibliography style (`uniadelaide.bst`) formatted on the Harvard citation style of the University of Adelaide. This style is origined from `agsm.bst` which also belongs to the Harvard Styling family.

Styles are based on the *Harvard referencing guide* (Last updated 20 April 2023).

See also: https://www.adelaide.edu.au/library/ua/media/4332/library-qrg-harvard-referencing.pdf

## Usage

1. Copy the `uniadelaide.bst` to the root of LaTeX project directory. Include `natlib` package with its configurations after the document class definition.

    ```latex
    \documentclass{...}
    % ...
    \usepackage{natbib}
    \setcitestyle{aysep={}}
    \bibliographystyle{uniadelaide}
    % ...
    \begin{document}
    ```

2. Add bibliography database file (ends with `.bib`) just before the end of `document` environment:

    ```latex
    % ...
    \bibliography{your-bibliograph-database-filename-without-extension}
    \end{document}
    ```

3. Use `\citep{bib-label}` to cite. Compile tex file with these commands:

    ```bash
    pdflatex main.tex
    bibtex main.aux
    pdflatex main.tex
    pdflatex main.tex
    ```

    or simply use `latexmk -pdf`. Then you got your work finished :)

## Changelog

1. Remove dot symbol after surname abbriviation
2. Remove parenthenses before and after year. You can restore them by adding

    ```latex
    \providecommand\adelaideyearleft{(}
    \providecommand\adelaideyearright[1]{)}
    ```

    before `\bibliographystyle{uniadelaide}`.

3. Remove dot between multiple surnames.
4. Support `type`/`vieweddate` label:

    |Symbols|Meaning|
    |-|-|
    |`@misc`| Bib item for website bibliograph |
    |`howpublished`| URL |
    |`title`| Title of webpage |
    |`type`| Title of website |
    |`vieweddate`| Date of webpage viewed |

    Example:

    ```bibtex
    @misc{wikibooksLaTeXDocStruct,
      author = {Wikibooks},
      title = {{L}a{T}e{X}/{D}ocument {S}tructure},
      howpublished = {\url{https://en.wikibooks.org/wiki/LaTeX/Document_Structure}},
      year = {2022},
      website = {Wikibooks},
      vieweddate = {13 May 2025}
    }
    ```

5. (Under dev.) Remove default sorting rule. The default order is by appearance.

## To-dos

Developing / Known issues:

- [x] **All types**: So far, if there are two/three authors, cites omit the second and the third authors using `et al.`. As expect, two or three authors should fully exists. Four or more authors should be in brief.
- [ ] **Webpage**: Some of website tags are not supported yet. Including `blog`, `tweet`, et al.
- [x] **Journal articles**: `[no pagination]` / `article no.` is not supported. (No plan to support)
- [ ] **A far more target**: Refactor on `biblatex` package. This is TBD.

Other types of styles are not tested yet.

Documenting / Publishing:

- [ ] Rewrite `main.tex` as a self-explained user/dev guide of `uniadelaide.bst`.
- [ ] Add all citations in the *Harvard referencing guide* into guide.
  - [x] **Journal articles**
  - [x] **Books**
  - [x] **Conference publications**
  - [x] **Newspaper or magazine article**
  - [ ] **Reference work**
  - [ ] **Dataset**
  - [ ] **Webpage**
  - [ ] **Social media**
  - [ ] **Audiovisual**
  - [ ] **Image**
  - [ ] **Other reference types**
- [ ] Publish as a public CTAN package.

## Contribute

If you find some issues, you can feedback via *GitHub Issues* on this repository.

If you have work out an approach to fix a issue (excellent!), you can make a pull request~

If you want to know the way working on Bibliography style (.bst) files, the best resource is *Tame the BeaST  --  The B to X of BibTeX* by Nicolas Markey. After install the TeXLive fully, the PDF version is located on `texlive\XXXX\texmf-dist\doc\bibtex\tamethebeast\ttb_en.pdf`. It will be a good start if you decide to learn a devil-like postfix language, so-called *Reverse Polish Notation*. Nicolas introduces it on chapter 16.
