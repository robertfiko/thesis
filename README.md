![CI status](https://github.com/mcserep/elteikthesis/workflows/Build%20LaTeX%20document/badge.svg)

See [English version](README_en.md).

# ELTE IK szakdolgozat és diplomamunka sablon

A [thesis_hu.tex](thesis_hu.tex) és a belőle előálló [thesis_hu.pdf](thesis_hu.pdf) szolgál kiindulási példaként.
A sablon alkalmazza a szakdolgozatra / diplomamunkára vonatkozó formai előírásokat, valamint elkészíti a megadott metaadatok alapján a címlapot. A példa dokumentum tartalmi fejezetei a BSc szakdolgozat tipikus felépítését tükrözik.
A formai megkötések az ELTE Informatikai Kar szabályzatában rögzítetteknek felelnek meg, de általánosan (a megfelelő módosításokkal) alkalmazható más egyetemek dolgozataihoz is.

A sablon tartalmazza az egy és két oldalas nyomtatáshoz szükséges beállításokat is (ld. `twoside` paraméter), alapértelmezetten a javasolt egy oldalas nyomtatásra konfigurált. (Érdemes figyelembe venni, hogy 20-nál kevesebb lapszám kemény kötésben furcsán mutat, továbbá az ábrák könnyen átütnek az általános 80g/m<sup>2</sup> fénymásolópapíron).
A sablon magyar és angol nyelvű dokumentumok elkészítését is támogatja (ld. `\documentlang` parancs).

## Fordítás

```bash
# thesis_hu.aux fájl generálása (PDF fájl még hibás hivatkozásokat fog tartalmazni)
pdflatex thesis_hu.tex
# Irodalomjegyzék generálása
bibtex thesis_hu
# Jelölésjegyzék generálása (ha szükséges)
makeindex -s nomencl.ist -t thesis_hu.nlg -o thesis_hu.nls thesis_hu.nlo
# Végleges PDF fájl generálása
pdflatex thesis_hu.tex
pdflatex thesis_hu.tex
```

**Megjegyzés:** az irodalomjegyzék változása esetén a `bibtex`, majd a `pdflatex` _kétszeri_ futtatása szükséges a helyes hivatkozások előállításához.

A fordításhoz tetszőleges fejlesztő környezet is használható (pl. [TexStudio](https://www.texstudio.org/)), ugyanezen utasítások kiadásával.

## Kódblokkok szintaxis kiemelése

A *minted* csomag támogatott a forráskódok szedésére és szintaxis kiemelésére. Használatához szükséges a Python interpreter és a `Pygments` csomag telepítése.
Lásd a `minted-integration.tex` fájlt példaként és ezt a [dokumentációt](https://www.overleaf.com/learn/latex/Code_Highlighting_with_minted).

## Fontosabb függőségi csomagok

**Képkezelés:**

* Minimális és maximális méret: [adjustbox](https://ctan.org/pkg/adjustbox)
* Alábrák: [subcaption](https://ctan.org/pkg/subcaption)
* Forgatás: [rotating](https://ctan.org/pkg/rotating)

**Táblázatkezelés:**

* Oszlopok és sorok egyesítése: [multirow](https://ctan.org/pkg/multirow)
* Tördelhető táblázat: [longtable](https://ctan.org/pkg/longtable)
* Cellatartalom vertikális igazítása: [array](https://ctan.org/pkg/array)
* Többsoros cellák (sortörés): [makecell](https://ctan.org/pkg/makecell)

**Felsorolások:**

* Szoros térközű felsorolások: [paralist](https://ctan.org/pkg/paralist)

**Matematika és algoritmusok:**

* Matematikai formulák: [amsmath](https://ctan.org/pkg/amsmath)
* Matematikai definíciók: [amsthm](https://ctan.org/pkg/amsthm)
* Matematikai szimbólumok: [amsfonts](https://ctan.org/pkg/amsfonts)
* Algoritmusok: [algpseudocode](https://www.ctan.org/pkg/algorithmicx)
* Kódblokkok: [listingsutf8](https://ctan.org/pkg/listingsutf8), [minted](https://ctan.org/pkg/minted)

**Egyebek:**

* Teendők: [todonotes](https://ctan.org/pkg/todonotes)

## Előre definiált tételszerű bekezdések

* *definition*: Definíció
* *theorem*: Tétel
* *remark*: Emlékeztető
* *note*: Megjegyzés
