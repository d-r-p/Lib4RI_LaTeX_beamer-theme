# Lib4RI LaTeX Beamer-Theme

Customisations of the beamer class for Lib4RI

## Introduction

This repository contains the customisations of the LaTeX beamer class for Lib4RI and an example to illustrate the theme's usage. The theme was originally written for Lib4RI's lecture series and purposefully mimicks (to some extent) the standard presentation template of Lib4RI.

## Installation

In addition to the five theme files (`beamercolorthemeLib4RI.sty`, `beamerinnerthemeLib4RI.sty`, `beamerthemeLib4RI.sty`, `beamerfontthemeLib4RI.sty`, `beamerouterthemeLib4RI.sty`), you will need the following resources:
* `by.eps`
* `Lib4RI.eps`

You can generate these resources as follows:
* `by.eps`:
    1. Download `by.svg` from `https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/by.svg`
    2. Convert to `eps` as follows:
        ```
        convert by.svg -resize 300x105 -density 600 by.eps
        ```
* `Lib4RI.eps`
    1. Open `MASTER_lib4ri_logo_cmyk.eps` (from the common directory) in, e.g., GIMP with resolution 200
    2. Change the white background color to `#f3efe6`
    3. Crop to just see the logo ("Lib4RI ////") without the writing underneath
    4. Save as `Lib4RI.eps` with no offset (the resulting image should roughly measure 1076x324 pixels with BoundingBox "0 0 388 117")

For best results, include the Lib4RI beamer theme through the file `useLib4RIbeamer.tex`.

## Usage

Generally, follow the example, which is split into four files:
* `example-common.tex`:
    This file contains the setup common to handout and presentation modes. In particular, it defines the frame titles that will follow your (sub-(sub-))sections, including numbering style. Moreover, it defines the `lfriexercise` counter and command (the latter increasing the former). It also defines the `lfrimodule`, `lfrilecture` and `lfrilecturepart` counters, which you can set to enumerate your lectures. Note that it could very well be re-used for other lectures.
* `example-frames.tex`:
    This file contains the individual frames. If you are not familiar with the beamer class, you can study it in order to understand how to define dynamic slides and how to produce good handouts for your presentation. Note how `\lfriexercise` is used. Also note that the last slide is removed in handout-mode. Finally, and just for this example, it contains a simplistic tool to retrieve individual sentences from paragraphs of the `lipsum` package (just ignore the relevant lines).
* `example-handout.tex`:
    LaTeX this file if you want to produce handouts.
* `example-presentation.tex`:
    LaTeX this file if you want to produce the presentation (i.e., dynamic slides).

_Note_: We assume that you are using `latex` mode, not `pdflatex` mode. From experience, the following command should compile your `<slides>.tex` (e.g., `example-presentation.tex`) resolving all labels:
```
latex <slides>.tex && latex <slides>.tex && latex <slides>.tex && dvips -o <slides>.ps <slides>.dvi && ps2pdf <slides>.ps && rm <slides>.ps
```

<br/>

> _This document is Copyright &copy; 2018 by d-r-p (Lib4RI) `<d-r-p@users.noreply.github.com>` and licensed under [CC&nbsp;BY&nbsp;4.0](https://creativecommons.org/licenses/by/4.0/)._
