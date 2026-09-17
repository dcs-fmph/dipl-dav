---
title: Úvod do LaTeXu
---

## Potrebný softvér

  - Linux: [TeXLive](http://en.wikipedia.org/wiki/TeX_Live)
  - Windows: [MikTeX](http://miktex.org/)
  - Existujú aj grafické a online prostredia na uľahčenie práce, viď
    [wikibooks](https://en.wikibooks.org/wiki/LaTeX/Installation),
    populárny je napríklad [Overleaf](https://www.overleaf.com/).

## Materiál k cvičeniu

  - [Materiál k cvičeniu](./files/Latex.zip) (ukážka textu v
    LaTeXu s vysvetlením použitých príkazov a s úlohami)
  - Môžete si pozrieť aj ukážku [prezentácie v balíčku beamer](/files/Latex-beamer.zip)

Ak chcete použiť [Overleaf](https://www.overleaf.com/),

  - Spravte si na ich stránke konto
  - Otvorte si materiál k cvičeniu na ich stránke
    <https://www.overleaf.com/read/srqjfjbrxfrx>
  - V položke Menu vľavo hore stlačte Copy Project, čo vytvorí vašu
    vlastnú kópiu materiálu, ktorú môžete na cvičení modifikovať

## Spúšťanie LaTeXu

Spúšťanie LaTeXu na príkazovom riadku v Linuxe, v adresári s
rozzipovaným materiálom k cvičeniu:

```bash
kate tutorial.tex &   # otvorime si editor so zdrojovym kodom 
pdflatex tutorial     # vytvorime tutorial.pdf
evince tutorial.pdf   # prehliadac pdf suborov
```

Pri použití literatúry pridajte príkaz

```bash
bibtex tutorial
```

Pri zložitejších súboroch je vhodné príkaz `pdflatex` spustiť viackrát.

## Zdroje informácií o LaTeXu

  - [LaTeX na Wikibooks](http://en.wikibooks.org/wiki/LaTeX) obsahuje aj
    popis mnohých užitočných knižníc makier
  - Príručka *Nie príliš stručný úvod do systému LaTeX2e* [v
    slovenčine](https://www.uiam.sk/~fikar/linux/Slshorte.pdf),
    [v angličtine](https://tobi.oetiker.ch/lshort/)
