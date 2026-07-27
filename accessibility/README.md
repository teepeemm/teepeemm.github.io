
Accessible PDF files using LaTeX
===========================
* The [MathFest poster](https://teepeemm.github.io/accessibility/poster/poster.pdf) and its [reading by NVDA in Foxit](https://teepeemm.github.io/accessibility/poster/poster.mp3)
* Make sure you have the latest TeX version, and have [updated your packages](https://tex.stackexchange.com/q/55437/107497)
* As the first commands, use
``` latex
\DocumentMetadata{
    lang=en,
    tagging=on,
    pdfstandard=ua-2,
  %  check-tagging-status,
    tagging-setup={
  %    math/alt/use,               % <=> Formulas must have description/alt text
      math/setup=mathml-SE
    }
}
\documentclass{...}
\usepackage{unicode-math}
```
* Compile with LuaLaTeX
* Any `\includegraphics`, `\tikz`, or `{tikzpicture}` or `{picture}` environments need `alt={...}` in the options (if the image is truly decorative, you can use the option `artifact` instead of `alt`; a different option is `actualtext={...}` if your image is really text in disguise).
[Other alt text guidelines](altText.html).
See `texdoc latex-lab-graphic` for more.
* Before tabular (or similar), use `\tagpdfsetup{table/header-rows={...},table/header-columns={...}}`. Use `\tagpdfsetup{table/multirow={...}}` within such cells.
See `texdoc latex-lab-table` for more.
* The `check-tagging-status` key will report [general class and package status](https://latex3.github.io/tagging-project/tagging-status/).
* [For more information](https://latex3.github.io/tagging-project/documentation/usage-instructions.html).
* If you must, you can [make the title act as a header](https://tex.stackexchange.com/a/758805/107497), but using `\section*` is better.
* [Further guidelines for presentations](ltx-talk.html)

Package/class substitutions:
-----------
* `enumitem` and `enumerate` -> `enumext` or `texdoc blocks-doc` for many new options
* `marginnote`, `marginfit`, and `marginfix` -> `marginalia` or `\marginpar`
* `titlesec` -> `\@startsection` (see `texdoc source2e`) or `texdoc latex-lab-sec-template` for many new options
* `beamer` -> `ltx-talk`

<!-- see also
 texdoc latex-lab-toc
 texdoc latex-lab-title
 texdoc documentmetadata-support-code
  -->

PDF Validators:
-----------
* [veraPDF](https://verapdf.org/software/) is used by the LaTeX team, has a command line interface, but reports the PDF address of any errors it finds
* [PDFix](https://pdfix.net/) uses the same algorithm as veraPDF, will show you where any errors are, but has no command line interface
* There are not many [other PDF validators](https://pdfa.org/accessible-math-in-pdf-finally/) that can handle math.
* [PDF validation false negatives](https://github.com/latex3/tagging-project/discussions/categories/issues-with-accessibility-checkers-and-other-at-software)
* FYI, [Ally's accessibility checklist](https://help.anthology.com/ally-lms/en/administrators/ally-accessibility-checklist.html).
Note that Ally appears many times in the false negatives list, and also will readily award false positives.
It's judgement probably shouldn't be trusted, but if it's judging you, you have to jump through a hoop and uncomment the `math/alt/use` line.

PDF Screen readers:
-----------
* NVDA or JAWS (both Windows only); Orca on Linux
* Adobe, Foxit, or Firefox
* [There are no others at this time](https://tex.stackexchange.com/a/755945/107497)

Other links:
-----------
* An ltx-talk [template](ltx-talk-und) for UND themed presentation
* [Test PDF files](https://texlive.net/tests/MathML/)
* [Tagging increases various system requirements](https://tex.stackexchange.com/a/751610/107497), so you may need [to increase](https://tex.stackexchange.com/a/741777/107497) [some limits](https://tex.stackexchange.com/a/518522/107497)

<!-- 

* https://accessibility.umn.edu/gaad/virtual-swag
* https://iu.instructure.com/courses/2325746/pages/creating-fully-tagged-pdf-slash-ua-2-accessible-documents-with-latex?module_item_id=35514589
* https://pdfa.org/resource/best-practice-guide-math-in-pdf/
* https://www.linkedin.com/feed/update/urn:li:activity:7444461479694639104

-->
