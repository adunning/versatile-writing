---
title: Versatile academic writing with Pandoc
author: Andrew Dunning
date: 14 December 2015
---

# Technology-independent writing

## Why not Word?

- Always focus on what will inspire you to write.
- There are many situations in which one needs to provide a document in multiple formats.
- From a technical point of view, there are several advantages to working with plain-text files:
    - You can see precisely what is in your files, and have complete control.
    - Easier to achieve accessibility.
    - Plain text has existed for decades.
    - Facilitates separation of content and presentation, and focus on structure.

## LaTeX

- A professional typesetting system, widely used for scientific writing.
- TeX begun in 1978; LaTeX is a macro language for TeX, begun in 1985.
- Drawback: can only produce PDFs.

## Markdown

- Lightweight markup language developed in 2004, designed to correspond to HTML.
- Introduction to basic markup: <http://markdowntutorial.com>
- Subsequently extended through many 'flavours', not entirely compatible with one another.

## Pandoc

- Document converter, begun in 2006 by John MacFarlane (now chair of philosophy at University of California Berkeley).
- Introduction: [Sustainable Authorship in Plain Text using Pandoc and Markdown](http://programminghistorian.org/lessons/sustainable-authorship-in-plain-text-using-pandoc-and-markdown)

## Example document

> **Test Document**
> 
> This is a *test* sentence.

## Word HTML output

```html
<body bgcolor=white lang=EN-US style='tab-interval:36.0pt'>

<div class=WordSection1>

<p class=MsoNormal><b style='mso-bidi-font-weight:normal'><span
style='mso-ansi-language:EN-US'>Test Document<o:p></o:p></span></b></p>

<p class=MsoNormal><span style='mso-ansi-language:EN-US'><o:p>&nbsp;</o:p></span></p>

<p class=MsoNormal><span style='mso-ansi-language:EN-US'>This is a <i
style='mso-bidi-font-style:normal'>test</i> sentence.<o:p></o:p></span></p>

</div>

</body>
```

## Semantic HTML output

```html
<h1>Test Document</h1>
<p>This is a <em>test</em> sentence.</p>
```

## Markdown input

```markdown
# Test Document

This is a *test* sentence.
```

# Setup

## What you'll need

1. A text editor. This can be anything you like, e.g. [Atom.io](https://atom.io), [TextMate 2](https://macromates.com) (Mac), or [Editorial](http://omz-software.com/editorial/) (iOS).
2. [Pandoc](http://pandoc.org), to convert your writing into the formats you want.
3. If you want to use a citation manager: [Zotero](https://www.zotero.org) provides the most flexibility.
4. Pandoc can [integrate with LaTeX](http://pandoc.org/installing.html) for creating well-typeset PDFs.

## Install Atom

<div class="notes">
Since Atom provides excellent support for Markdown and is cross-platform and open-source, we're going to focus on it in this tutorial. It is intended as a minimalist basis onto which one can add the pieces needed.
</div>

1. Download and install the appropriate version of [Atom](https://atom.io) for your system.
2. Add these packages by opening the Atom preferences, going to the Install screen, and searching for the following:
    - markdown-writer
    - zotero-citations

---

3. Other useful packages:
    - dictionary (OS X Dictionary integration)
    - wordcount
    - zen (full-screen writing)
    - language-pfm (better syntax highlighting: disable language-gfm package if used)
    - markdown-folder
    - markdown-mindmap
    - markdown-preview-plus (Markdown preview using Pandoc)
    
## Configure Atom Packages

1. In the settings screen for Zotero Citations, change the citation style to 'pandoc'.
2. To set up standard keyboard shortcuts, type <key>Cmd</key>/<key>Ctrl</key>+<key>Shift</key>+<key>P</key> to open the command window, and select 'Markdown Writer: Create Default keymaps'.

## Install Pandoc

- Install using the [Pandoc package](http://pandoc.org/installing.html).
- Mac: package also available, but recommended to install using [Homebrew](http://brew.sh), a manager for command-line tools.

## Install Zotero

- Download [Zotero](https://www.zotero.org/download/).
- Install the [Better BibTeX](https://zotplus.github.io/better-bibtex/) add-on.

# Start writing

## Basic syntax

1. Create a new document in Atom and save it somewhere with a `.md` extension.
2. Open the command window (<key>Cmd</key>/<key>Ctrl</key>+<key>Shift</key>+<key>P</key>) and choose 'Markdown Preview'.

```markdown
*italic* or _italic_

**bold**

New paragraphs are indicated by two line breaks.
```

## Lists

```markdown
- Item 1
- Item 2
- Item 3
```

```markdown
1. Item 1
2. Item 2
3. Item 3
```

## Headings

```markdown
# Heading 1

Text.

## Heading 2

Text.

### Heading 3

Text.
```

## Block Quotation

```markdown
Text.

> Quoted text.
```

## Metadata

```yaml
---
title: My Horrible Life
author: Peter Abelard
date: 14 December 1115
abstract: |
    Explanation of the pure and unappreciated
    genius of the author.
---
```

## Comments

```markdown
<!-- This text will not be visible. -->
```

# Convert a document

## Open the Terminal

- Programs are executed on the command line by typing their name, followed by 'arguments' (i.e. the content they are to manipulate) and 'flags' (options to be used).
    - Mac: Terminal (in the Utilities folder)
    - Windows: Command Prompt or PowerShell

- Type `pandoc`: nothing will happen, since it needs text to work with.
- Type something into the prompt. To end the transmission, type <key>Ctrl</key>+D (<key>Ctrl</key>+Z on Windows).
- Pandoc will provide the HTML equivalent of what you just typed.

## Open the folder in the terminal

### Mac

- Drag the icon for the folder you want to work with onto the Terminal icon in the Dock.

### Windows

- Right-click in the folder with the <key>shift</key> key held down
- Choose the 'Open in Command Prompt' option.

## Convert a document to HTML

- To convert a file named `test.md` into HTML format:

> pandoc test.md -o test.html -sS

- The `-sS` flags are short forms for the `smart` and `standalone` options, which enable smart typography and HTML heading information (document will be a fragment otherwise).

## Convert a Word document to Markdown

> pandoc word-test.docx -o word-test.md -sS --atx-headers --no-wrap

- There are two different methods of writing headings in Markdown; `--atx-headers` uses the hash characters.
- 

## Other formats

### HTML5

> pandoc test.md -o test.html -sS -t html5

### Word

> pandoc test.md -o test.docx -sS

### EPUB

> pandoc test.md -o test.epub -sS

# Citations

## Add a citation

Pandoc allows one to write citations that will come out comprehensibly in any citation format.

1. Add an item to Zotero (e.g. click on the magic wand button and type the ISBN 0-19-814456-3).
2. In Atom, open the command window (<key>Cmd</key>/<key>Ctrl</key>+<key>Shift</key>+<key>P</key>), and look for 'Zotero Citations: Pick'.
3. A window will appear allowing you to search for one or more items in the Zotero library.
4. Pressing <key>Return</key> will add a citation key to your document.

## Save the bibliography

- Export the bibliographical data from Zotero: right-click on 'My Library', choose 'Export Library', and the 'Better CSL JSON' format.
    - Click the 'keep updated' option to have Zotero automatically update this file whenever a change is made to its database. You can then place this file in a central location and use it for all projects.

## Convert a document with citations'

- If you are converting a file named `test.md` to HTML and saved your bibliography in the same folder, named `library.json`:

    > pandoc test.md -o test.html -sS --bibliography=library.json

    A plain file name will only work if it is in the current folder. To use a file from somewhere else, drag onto the terminal window to insert its exact path.

## Change the citation style

1. Download a citation style from the [Zotero style repository](https://www.zotero.org/styles).
2. Change the citation style:

    > pandoc test.md -o test.html -sS --bibliography=library.json --csl=chicago-fullnote-bibliography.csl

## In-text reference

```markdown
Catullus is imprudent, as @reynolds:1983texts [p. 21] argue.
```

Chicago author-date
: Catullus is imprudent, as Reynolds and Marshall (1983, 21) argue.

Chicago full note
: Catullus is imprudent, as L.D. Reynolds and Peter K. Marshall, eds. [**footnote**: *Texts and Transmission: A Survey of the Latin Classics* (Oxford: Clarendon Press, 1983), 21.] argue.

## Footnote/parenthetical reference

```markdown
Horace is highly corrupt [see @reynolds:1983texts, p. 21].
```

Chicago author-date
: Horace is highly corrupt (see Reynolds and Marshall 1983, 21).

Chicago full note
:  Horace is highly corrupt. [**footnote**: See L.D. Reynolds and Peter K. Marshall, eds., *Texts and Transmission: A Survey of the Latin Classics* (Oxford: Clarendon Press, 1983), 21.]

## Suppress author

```markdown
Reynolds and Marshall call Tacitus 'appalling'
[-@reynolds:1983texts, p. 21].
```

Chicago author-date
: Reynolds and Marshall call Tacitus 'appalling' (1983, 21).

Chicago full note
:  Reynolds and Marshall call Tacitus 'appalling'. [**footnote**: *Texts and Transmission: A Survey of the Latin Classics* (Oxford: Clarendon Press, 1983), 21.]

# Slides

## HTML slides

- Uses a presentation framework such as [reveal.js](http://lab.hakim.se/reveal-js/) to display a webpage as a series of slides.
- More accessible for users of screen readers than a PDF.
- Notes can be generated from the same file. (Anything enclosed in `<div class="notes">` … `</div>` will not appear on the slide.)

## Convert to reveal.js

- New slides are generated based on headings and horizontal rules (`---`).

    > pandoc versatile-writing.md -o versatile-writing.html -sS -t revealjs
