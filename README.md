# ISC Chemistry - Solved School Papers

Two Heritage School Class XII Chemistry papers, answered in full, as a static
site. Open `index.html`.

Each answer runs **Question -> Formula used -> Answer -> Why -> NCERT**:

- the **formula** is shown in its own box *before* any arithmetic, for every
  numerical;
- the **why** says in a sentence or two what the question was really testing;
- the **NCERT** line is a button - clicking it opens that chapter's PDF **at the
  cited page** in a panel beside the answer. Press `Esc` to close it.

| Paper | Marks | Answers |
|---|---|---|
| [First Term 2024-25](heritage-2024-25.html) | 70 | 38 |
| [Pre-Board 2016-17](heritage-2016-17.html) | 70 | 50 |

## A caveat about the 2016-17 paper

It is on the **old syllabus**. The 2023 rationalisation removed Solid State,
ionic equilibrium, Surface Chemistry, the p-Block, metallurgy and Polymers from
the NCERT Class XII book, so about a third of that paper has **no NCERT page**.
Those answers say which chapter was removed instead of citing one.

## NCERT page numbers

Page numbers are the pages **printed in the book** (Class XII Chemistry, Parts I
and II, 2026-27 reprint). Each chapter is a separate PDF, so a link converts the
printed page to that file's own page index:

    pdf_page = printed_page - (first printed page of the unit) + 1

| Unit | Title | Printed pages | File |
|---|---|---|---|
| Ch 1 | Solutions | 1-30 | `ncert/lech101.pdf` |
| Ch 2 | Electrochemistry | 31-60 | `ncert/lech102.pdf` |
| Ch 3 | Chemical Kinetics | 61-88 | `ncert/lech103.pdf` |
| Ch 4 | The d- and f-Block Elements | 89-117 | `ncert/lech104.pdf` |
| Ch 5 | Coordination Compounds | 118-140 | `ncert/lech105.pdf` |
| Ch 6 | Haloalkanes and Haloarenes | 159-192 | `ncert/lech201.pdf` |
| Ch 7 | Alcohols, Phenols and Ethers | 193-226 | `ncert/lech202.pdf` |
| Ch 8 | Aldehydes, Ketones and Carboxylic Acids | 227-258 | `ncert/lech203.pdf` |
| Ch 9 | Amines | 259-280 | `ncert/lech204.pdf` |
| Ch 10 | Biomolecules | 281-302 | `ncert/lech205.pdf` |

## Serving it

Static and fully relative - push the folder to GitHub and enable **Pages**.

To read it locally, serve it rather than opening the file directly:

    python3 -m http.server

then visit `localhost:8000`. Opening `index.html` straight from disk mostly
works, but some browsers refuse to render a PDF inside an iframe over `file://`;
the panel's **Open in new tab** button covers that case.

## Regenerating

The site is generated, not hand-edited. From `Revision/src/`:

    python3 build_heritage_2024.py     # the 2024-25 solutions
    python3 build_heritage_2016.py     # the 2016-17 solutions
    python3 build_site.py              # this folder
    python3 verify_site.py --ui        # 102 checks, incl. a real browser

`verify_heritage_papers.py` recomputes every numerical from the data in the
question and re-greps every NCERT citation in the chapter PDF, so a page number
cannot be invented or go stale. `verify_site.py` additionally opens the page
each link points at and reads the printed folio back off it.
