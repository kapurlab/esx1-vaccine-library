# ESX-1 Vaccine Library

Annotated reference shelf for the ESX-1 recombinant BCG literature and the
bovine and human TB vaccine work around it.

Maintained by the Kapur Lab, Penn State.

## What this repo is

One file. `index.html` is self-contained: no build step, no dependencies, no
framework. Fonts load from Google Fonts; styles, reference data and filtering
are all inline. Do not split it into partials or add tooling. The single file
is the feature.

## Live site

    https://kapurlab.github.io/esx1-vaccine-library/

Served by GitHub Pages from `main`, root folder.

## Adding or editing an entry

Edit `index.html` and commit to `main`. Pages redeploys in about a minute.

The data is a JavaScript array named `R`, starting around line 280. Sections are
declared in the `S` array above it. Add your entry inside `R`, under the section
you want, in the order you want it to appear.

    {s:"bovine", key:1, a:"Fromsa A, Willgert K, Srinivasan S, et al.",
     y:2024, ti:"BCG vaccination reduces bovine tuberculosis transmission",
     j:"Science", c:"383(6690):eadl3962",
     doi:"10.1126/science.adl3962", pmid:"38547287", pmc:"<pmcid>",
     ac:"oa", drv:"<google-drive-file-id>",
     n:"Annotation goes here."},

Fields:

| Field | Meaning |
| --- | --- |
| `s` | Section key, one of the `k` values in `S` |
| `a` | Author string, as you want it displayed |
| `y` | Year |
| `ti` | Title, verbatim |
| `j` | Journal |
| `c` | Volume, issue and pages |
| `n` | Annotation. `<em>` and `<b>` are allowed |
| `key` | `1` marks a key reference (larger title, tinted card) |
| `ac` | Access label: `oa`, `pmc`, or `sub` |
| `doi` | DOI without the `https://doi.org/` prefix |
| `pmid` | PubMed ID |
| `pmc` | PMCID including the `PMC` prefix |
| `url` | Any other full-text URL |
| `drv` | Google Drive **file id**, not a full URL |
| `ill` | `1` if the local copy is an interlibrary loan scan |
| `cap` | `1` if the local copy is a browser capture, not the publisher PDF |

`ill` or `cap` draws the dashed left rule and adds a caveat chip. Omit any field
that does not apply; missing links are skipped.

Section keys: `esx1-rbcg`, `esx1-biology`, `phop`, `tools`, `bovine`, `diva`,
`human`, `route`, `epi`, `platform`.

The reference count in the masthead is computed at runtime, so it updates
itself. The compiled date is hard-coded in the `<header>`; change it by hand.

## Suggesting a paper or an edit

Add a row to the intake sheet, linked from the page header:

    https://docs.google.com/spreadsheets/d/1Brz2rFIj089tXB50vayIApwt9XnP1Lsvv1P-tpZScTo/edit

Columns: DOI or URL, section, suggested by, date, why it belongs, status. The
"why it belongs" text becomes the seed for the annotation. Mark a row `added`
once its entry is in `index.html`.

Discussion belongs in the lab's Google Group, not here. This repository is
public, so issues are world-readable: do not post unpublished data, embargoed
results, or anything from a manuscript under review.

## PDFs

Full texts live in a shared Google Drive folder, not in this repo. Drive
permissions control who can open them, and the `PDF in Drive` links fail by
design for anyone without folder access. Never commit publisher PDFs here.
