---
title: LaTeX pre bakalársku prácu
---

Informácie pre začiatočníkov nájdete na stránke [Úvod do LaTeXu](./Uvod_do_LaTeXu.md). Na tejto stránke sa snažíme zhrnúť
informácie špecificky potrebné k bakalárskej práci.

## Kostra práce

Ak chcete použiť LaTeX, môžete si stiahnuť [kostru bakalárskej práce](./files/Praca.zip), ktorá obsahuje požadovaný formát
prvých strán a ukážky užitočných príkazov.
  - Ako alternatívu môžete tiež použiť kostru, ktorú spravili nedávni
    absolventi: <https://github.com/davidmisiak/thesis-template>

Kostra obsahuje niekoľko súborov:
  - súbor `main.tex`: hlavný súbor, v ktorom je kostra práce
  - súbor `main-en.tex`: ukážka, ako adaptovať hlavný súbor pre práce v
    angličtine
  - ďalšie súbory `.tex`: jednotlivé kapitoly práce - úvod, kapitola,
    latex, záver, prílohy
  - `literatúra.bib`: zoznam literatúry v BibTeXu
  - prečinok `images` s obrázkami a zadaním v pdf formáte

Vytvorenie pdf (ak používate príkazový riadok):

```bash
pdflatex main.tex   # pri prvom spustení sa uložia potrebné odkazy
bibtex main         # spracovanie literatúry
pdflatex main.tex   # pri druhom spustení sa vytvoria odkazy v texte, ale môžu sa ešte posunúť strany
pdflatex main.tex   # preto pre istotu zopakujeme ešte raz
```

  - Informácie o obsahu, odkazoch a podobne si LaTeX ukladá do pomocných
    súborov, napr. `main.aux`, `main.toc`
  - Tento postup je zapísaný v súbore `Makefile`, stačí teda spustiť
    príkaz `make`

## Členenie práce

Bakalárska práca je vlastne kniha, začína riadkom

    \documentclass[12pt, twoside]{book}

a tým pádom sa očakáva členenie na kapitoly, podkapitoly, atď.

  - Kapitola `\chapter{Nazov}`
  - Podkapitola `\section{Nazov}`
  - Ešte podrobnejšie členenie `\subsection{Nazov}`
  - Odstavec s malým nadpisom `\paragraph{Nazov}`
  - Ak niečo nechceme číslovať, použijeme \*, avšak, ak to chceme v
    obsahu, musíme to do neho pridať
```latex
\chapter*{Úvod}
\addcontentsline{toc}{chapter}{Úvod}
```

## Číslovanie a odkazy v rámci textu

  - Latex čísluje kapitoly a podkapitoly, obrázky, tabuľky, vzorce,
    definície, lemy atď.
  - Na jednotlivé súčasti textu je vhodné odkazovať sa číslom
  - Aby sme nemuseli čísla ručne meniť, požijeme dvojicu príkazov
    `\label` a `\ref`.

Časti textu, na ktorú sa chceme odkazovať vytvoríme názov pomocou
`\label`:
```latex
\chapter{Implementácia}
\label{chap:impl}
```

Ak sa na túto kapitolu teraz chceme odvolať, použijeme `\ref`:

    Ako konkrétne sme algoritmus implementovali, vysvetlíme v kapitole \ref{chap:impl}.

## Obrázky, tabuľky

  - Obrázky a tabuľky sa vkladajú v "plávajúcich" (floating)
    prostrediach `figure` a `table`, ktoré LaTeX umiestni na vhodné
    miesto (vrch aktuálnej strany, prípadne ďalšej strany, alebo aj
    samostatná strana).
  - V rámci tohto prostredia vkladáme pod obrázok alebo tabuľku aj popis
    (caption).
  - LaTex obrázky a tabuľky čísluje.
  - Na každý obrázok a tabuľku by ste sa mali v texte aspoň raz odkázať
    (pomocou `\ref`)
  - `\label` dajte až za `\caption`

```latex
\begin{figure}
  \begin{center}
     \includegraphics[width=0.5\textwidth]{obrazok.png}
     \caption{Príklad kostry grafu.}\label{fig:kostra}
  \end{center}
\end{figure} 

\begin{table}
  \begin{center}
    \caption{A simple table}\label{tab:simple}
    \begin{tabular}{| l c r |}
      \hline
      1 & 2 & 3 \\
      4 & 5 & 6 \\
      7 & 8 & 9 \\
      \hline
    \end{tabular}
  \end{center}
\end{table}
```

## Práca s literatúrou

  - Vhodné je použiť systém
    [BibTeX](http://en.wikipedia.org/wiki/BibTeX)
  - V .bib súbore si spravíme zoznam použitých zdrojov, každému dáme
    label
  - Záznamy vo formáte pre BibTeX si vieme stiahnuť z niektorých stránok
    (napr. [Google scholar](http://scholar.google.com/)) alebo vytvoriť
    [nástrojmi na prácu s
    literatúrou](./Praca_s_literaturou.html#podporný-softvér)
  - V texte odkazujeme na zdroje pomocou `\cite{label}`, každý zdroj by
    sme mali aspoň raz zacitovať

Časté chyby:

  - BibTeX mení písmená v názve článku na malé, čo je problém pri
    skratkách a vlastných menách v názvoch. Vložte tieto slová do {},
    napríklad `title="Theano: a {CPU} and {GPU} math expression compiler"`.
  - Mená autorov treba písať v poradí krstné meno priezvisko alebo
    priezvisko, krstné meno (t.j. `Jozef Mrkvička` alebo `Mrkvička, Jozef`).
  - Autorov oddeľujte slovom `and`, čiarka sa považuje za oddelenie
    priezviska a mena.
  - Ak je autorom organizácia s viacslovným názvom, dajte ju do {}, napr
    `author="{ENCODE Project Consortium}"`
  - Ak je autorov veľa, uveďte prvého a et al., čo dostanete v BibTeXu
    pomocou `and others`.

## Zaujímavé balíčky

Tu postupne pribúda zoznam balíčkov v LaTeXu, ktoré
považujeme za užitočné, alebo ich odporučíte spolužiakom vy.

  - [Balíček subcaption](https://ctan.org/pkg/subcaption) urobí do
    jedného obrázku viac podobrázkov
  - [Balíček
    listings](http://texdoc.net/texmf-dist/doc/latex/listings/listings.pdf)
    highlightovanie a formátovanie zdrojového kódu vkladaného do LaTeXu
  - [Návod](https://www.overleaf.com/learn/latex/Algorithms) na
    formátovanie pseudokódu
  - [Table Generator](https://www.tablesgenerator.com/) stránka na
    generovanie LaTeXových tabuliek prekopírovaním tabuľky z
    kancelárskeho softvéru
  - [TikZ](https://pgf-tikz.github.io/pgf/pgfmanual.pdf) je balíček na
    kreslenie obrázkov a diagramov v LaTeXu, hodí sa napríklad na grafy (vrcholy, hrany)
    a konečné automaty

## Kontrola originality záverečnej práce

Keďže sa práca kontroluje automaticky v centrálnom registri, je
potrebné, aby bola vo formáte PDF, ktorý nesmie byť zaheslovaný a musí
sa dať previesť na čistý text.

  - prevod na text si môžete otestovať [na stránke CRZP](http://testdoc.crzp.sk/?fn=main).

Rozhodne zatiaľ neodovzdávajte prácu do AISu. Prácu
odovzdajte a označte v systéme AiS2 ako finálnu až po ubezpečení sa, že
je to konečná verzia a že v nej nebudete robiť ďalšie úpravy. **Prácu
môže študent označiť ako finálnu IBA 1x.**

Najnovšie verzie pdflatex-u by mali vytvoriť pdf súbor, ktorý sa dá
dobre previesť na čistý text, avšak pri starších verziách môžete mať
problémy s kódovaním diakritiky - výsledok môže byť napr.

  - `Kl’uˇov´ slov´: jedno, druh´, tretie (pr´ ´c e a e ıpadne ˇtvrt´,
    piate) s e`
  - `Kl ’´uˇcov´e slov´a: jedno, druh´e, tretie (pr´ıpadne ˇstvrt´e,
    piate)`

Pomôcť vám môže nainštalovanie balíčku fontov [cm-super](https://www.ctan.org/pkg/cm-super).
