# ISC Chemistry — Class 12, First Term

A static site: timed papers to sit, revision decks, and the school papers worked
through. Open `index.html`.

Three hub pages, cross-linked by the bar at the top of each:

| Page | What is on it |
|---|---|
| `index.html` | landing page — two tiles, **Sit a paper** and **Revise** |
| `tests.html` | **everything timed**: 4 subject papers, 3 other papers, 3 timed drills |
| `revision.html` | **nothing timed**: decks, notes, solved papers, untimed drills, PDFs |

## What's here

| | |
|---|---|
| **Sit a paper** | 4 subject papers (Physical 40Q/60min, Organic 40Q/60min, Coordination 25Q/40min, Biomolecules 25Q/40min), plus the longer Physical test and two organic tests |
| **Revise** | First Term revision deck (210 questions), concepts deck (120 concepts), Coordination notes, Haloalkanes deck, Alcohols reading page, and the two Heritage papers solved |
| **Drill** | Three Kinetics + Organic question banks, each as a learn page and a timed test |
| **Documents** | Revision PDFs, the coordination notes in three forms, and the school papers with their solutions |

## The timed papers

Each one **locks when you start**:

- answers change freely and **nothing is marked until you submit**;
- closing the tab, reloading or navigating away **submits the paper** with whatever has been answered;
- switching tab or minimising is counted — two warnings, then the third submits it.

On submission you get the mark, a chapter breakdown, and a worked explanation on
**every** question, each naming where it came from.

## NCERT links

`ncert/` holds the ten NCERT Class XII chapter PDFs. The Coordination notes and
the two Heritage solved papers link into them at the exact page, converting the
book's printed page to that file's page index. Unit page ranges: Ch 1 1–30,
Ch 2 31–60, Ch 3 61–88, Ch 4 89–117, Ch 5 118–140, Ch 6 159–192, Ch 7 193–226,
Ch 8 227–258, Ch 9 259–280, Ch 10 281–302.

## Serving it

Static and fully relative — push the folder to GitHub and enable **Pages**.

To read it locally, serve it rather than opening the file directly:

    python3 -m http.server

then visit `localhost:8000`. Opening `index.html` from disk mostly works, but
some browsers refuse to render a PDF inside an iframe over `file://`.

Note the folder is **`ncert/`, lowercase**. GitHub Pages is case-sensitive, so
links must match exactly; the build normalises them.

## Regenerating

The site is generated, not hand-edited. From `../src/`:

    python3 build_subject_papers.py   # the four subject papers + Chemistry/index.html
    python3 build_site_full.py        # assembles this folder and its index
    python3 verify_site_full.py       # checks every internal link resolves
