# Vjezba - Kontakt Forma

Kratka dokumentacija za projekt "Vjezba-Kontakt-Forma".

## Pregled
Ovo je mala web stranica za prikaz kurseva i nekoliko interaktivnih mini-aplikacija (Student Fun Zone). Sadrži statičke HTML stranice te jednostavnu klijentsku logiku u JavaScriptu (nijedan server nije potreban).

## Glavne funkcionalnosti
- Statične stranice:
  - `index.html` — početna stranica (O kursevima)
  - `popis.html` — popis kurseva
  - `raspored.html` — raspored kurseva
  - `kontakt.html` — kontakt stranica s kontakt formom i klijentskom validacijom
  - `StudentFunZone.html` — stranica s igricama i interaktivnim alatima

- Kontakt forma (`kontakt.html`):
  - Polja: ime i prezime (required, min length 5), email (regex validacija), telefon (regex/digits validacija), poruka (required), checkbox `terms` (required), checkbox `newsletter` (opcionalno).
  - Validacija je izvedena u klijentskom JavaScriptu (sprečava slanje ako su polja neispravna) i pokazuje poruke o greškama.

- Student Fun Zone (ugrađeni sadržaji kroz jedan iframe):
  - Kviz — `kviz_index.html` (otvara se unutar stranice)
  - Bingo — `bingo/index.html` (otvara se unutar stranice)
  - Interaktivni Vision Board — `visionboard/visionboard.html` (koristi slike iz foldera `visionboard/` i lokalStorage za spremanje)
  - Interaktivni Whiteboard — `whiteboard/whiteboard.html` (canvas za crtanje, spremanje kao PNG)
  - Kanban ploča — `kanban/kanban.html` (jednostavna drag/drop ploča, export koristeći `html2canvas` CDN)

  Svi gore navedeni alati se učitavaju u isti iframe iz `StudentFunZone.html` preko gumba koji imaju `data-src` atribut.

## Tehnologije
- HTML5
- CSS3 (jedan glavni stylesheet: `css/izgled.css` i lokalni stilovi unutar podfoldera kao `visionboard/style.css`, `whiteboard/whiteboard_stil.css`, `kanban/kanban_ploca_stil.css`)
- JavaScript (vanjski skripti u folderima, bez backend-a)
- html2canvas (CDN) — koristi se u Kanban za spremanje kao PNG

## Struktura projekta (važni fajlovi)
```
/ (root)
  index.html
  popis.html
  raspored.html
  kontakt.html
  StudentFunZone.html
  css/izgled.css
  favicon.ico
  slike/...
  bingo/index.html
  kviz_index.html
  visionboard/
    visionboard.html
    javascript.js
    style.css
    slika1.png ...
  whiteboard/
    whiteboard.html
    whiteboard_skripta.js
    whiteboard_stil.css
  kanban/
    kanban.html
    kanban_ploca_skripta.js
    kanban_ploca_stil.css
```

## Spremanje i vraćanje podataka (lokalno)
- Vision Board sprema elemente u `localStorage` pod ključem `visionBoardItems`.
- Whiteboard omogućava spremanje slike iz canvas-a kao PNG (preuzimanje), ali ne radi automatsko lokalStorage snapshot po zadanoj implementaciji.
- Kanban koristi `html2canvas` za eksport slike.


