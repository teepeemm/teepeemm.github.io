
Accessible Presentations using LaTeX
===========================
* Follow all of the guidelines for [accessible PDFs](./).
* As the first commands, use
``` latex
\DocumentMetadata{
    lang=en,
    tagging=on,
    pdfstandard=ua-2,
  %  check-tagging-status,
    tagging-setup={
  %    math/alt/use,               % <=> Formulas must have description/alt text
  %    role/new-tag=frametitle/H1, % <=> headings must begin at level 1
      math/setup=mathml-SE
    }
}
\documentclass{ltx-talk}
```

Template Defaults:
-----------

### `\ShowTemplateDefaults{header}{talk}`

|Key|Type|Default|
|---|----|-------|
|color|tokenlist|structure (= rgb(0.2,0.2,0.7) =blue)|
|font|tokenlist|`\normalfont`|
|height|length|`\Gm@tmargin +\headsep` = 10mm + 2mm|
|left-hspace|skip|`\Gm@lmargin` = 10mm|
|print-frame-title|boolean|true|
|right-hspace|skip|`\Gm@rmargin` = 10mm|
|background-color|tokenlist||

To make adjustments, call `\EditInstance{header}{std}{⟨key=value⟩}` or
`\EditInstance{frametitle}{header}{font=⟨...⟩}`.

### `\ShowTemplateDefaults{footer}{talk}`

|Key|Type|Default|
|---|----|-------|
|font|tokenlist|`\tiny`|
|left-skip|length|`\Gm@lmargin` = 10mm|
|right-skip|length|`\Gm@rmargin` = 10mm|
|separator|tokenlist|`\hfil`|
|background-color|tokenlist||
|color|tokenlist||
|element-order|commalist||

To make adjustments, call `\EditInstance{footer}{std}{⟨key=value⟩}`.
Available elements are date, author, title, institute, & framenumber

### `\maketitle`

Default `\maketitle` is equivalent to
``` tex
\maketitle[
  element-order        = { title, subtitle, author, institute, date },
  framestyle           = talk,
  horizontal-alignment = center,
  vertical-alignment   = center
]
```
`framestyle` is `pagestyle`, and can also be `plain`, `empty`, or `wallpaper` (header & footer have color but no text).

Creating Elements
-----------------

### Logo in the header
``` tex
\newsavebox\logobox
\savebox\logobox{\includegraphics[artifact,height=\baselineskip]{logofile}}
% possibly after \maketitle frame
\AddToHook{shipout/foreground}{\put(\paperwidth - \wd\logobox - 10mm,-8.5mm){\usebox\logobox}}
```

### Custom footer element
``` tex
\DeclareInstance{footer-element}{myelement}{talk}{...}
\ExpandArgs{c}\newcommand{@myelement}{...}
``` 
For example,
`\ExpandArgs{c}\newcommand{@frameoftotal}{\arabic{frame}/\RefProperty{lastpage}{totalframes}}`.
(If you also define `\@shortmyelement`, ltx-talk will use that.)

### Custom title element
``` tex
\DeclareInstance{titlepage-element}{myelement}{talk}{...}
\ExpandArgs{c}\newcommand{@myelement}{...}
```

Other
----------

### Float Positioning

`\EditInstance{floatenv}{std}{horizontal-alignment = ⟨alignment⟩}`,
where `⟨alignment⟩` is left (default), center, or right.

### Opacity

`\EditInstance{hidden}{std}{opacity=⟨value⟩}`, where 0≤`⟨value⟩`≤1, with the default 0 being "invisible".
