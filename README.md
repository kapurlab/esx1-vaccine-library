# ESX-1 Vaccine Library

Annotated reference shelf for the ESX-1 recombinant BCG literature and the
bovine and human TB vaccine work around it.

Maintained by the Kapur Lab, Penn State.

## What this repo is

One file. `index.html` is self-contained: no build step, no bundler, no
framework. Styles, reference data and filtering are all inline. Do not split it
into partials or add tooling. The single file is the feature.

Two things load from outside: the fonts, from Google Fonts, and the Hypothesis
annotation client, from `hypothes.is`. Nothing else is fetched at runtime.

## Live site

    https://kapurlab.github.io/esx1-vaccine-library/

Served by GitHub Pages from `main`, root folder. A push reaches the live page in
about a minute, though the edge can serve the previous copy for a few seconds
after the deployment is recorded.

## Adding or editing an entry

Edit `index.html` and commit to `main`.

The data is a JavaScript array named `R`, at line 320. Sections are declared in
the `S` array at line 307. Add your entry inside `R`, under the section you
want, in the order you want it to appear.

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
that does not apply; missing links are skipped. The two `ill` entries carry no
`drv` on purpose, because their scans are restricted and the link would fail for
everyone but the owner.

Section keys: `esx1-rbcg`, `esx1-biology`, `phop`, `tools`, `bovine`, `diva`,
`human`, `route`, `epi`, `platform`.

The title bar counts, the per-section counts in the rail and the section jump
menu are all computed at runtime. The compiled date is hard-coded in the
`<header>`; change it by hand.

The page opens on the key papers filter, not on the full list. An entry without
`key` is present but hidden until the reader changes the filter, and text that
is filtered out cannot be selected, so it cannot be annotated either.

## Writing an annotation

The `n` field carries the claim, not a summary of the abstract. Say what the
study established and why it belongs on this shelf. Two to four sentences.

Check every fact against the paper itself, through the NCBI E-utilities or the
PubMed Central full text. Do not reconstruct an identifier, a sample size or an
effect estimate from memory. If a number cannot be confirmed, leave it out.

Report the effect estimate and the population when they are the point of the
paper, and name the model organism where it limits the claim. Do not call
evidence robust or compelling, and keep `significant` to its statistical sense.

Plain, direct English, American spelling. No em dashes. Most sentences under 25
words, one claim each, active voice, no sentence fragments. Titles, journal
names and author strings stay verbatim, including any British spelling or en
dash inside them.

## Suggesting a paper or an edit

Add a row to the intake sheet, linked from the page header:

    https://docs.google.com/spreadsheets/d/1Brz2rFIj089tXB50vayIApwt9XnP1Lsvv1P-tpZScTo/edit

Columns: DOI or URL, section, suggested by, date, why it belongs, status. The
"why it belongs" text becomes the seed for the annotation. Mark a row `added`
once its entry is in `index.html`.

Discussion belongs in the lab's Google Group, not here. This repository is
public, so issues are world-readable: do not post unpublished data, embargoed
results, or anything from a manuscript under review.

## Comments

Comments are Hypothesis annotations. The page loads the client, so a reader can
open the sidebar without installing anything. Writing an annotation needs a
Hypothesis account. A dismissible notice under the masthead explains the steps,
and the reader's choice to hide it is kept in their own browser.

Discussion belongs in the private `Beyond BCG` group, not the public layer.
Anything posted to Public is world-readable and appears in Hypothesis search.
Select the group in the sidebar before you write.

The join link is not published here, and it should not be. Clicking that link
and logging in joins the group at once, with no approval step, so anyone holding
it can read every annotation. It lives in a document inside the shared Drive
folder, and the `Join the annotation group` link in the masthead points at that
document. Drive decides who may open it, which a static page cannot do. For the
same reason the client is configured without a `groupsAllowlist`, since that
setting would put the group id in the page source.

Annotations anchor to quoted text. Rewriting an entry's annotation orphans any
comment attached to the old wording, so expect to lose anchors when text is
revised. Circulate the bare URL, since a query string may register as a
different document.

The client overlays the page rather than reflowing it, and it reserves less
margin than its sidebar occupies. The page measures the sidebar and holds its
own content clear, dropping to a single column when the room left falls below
1100px. That code sits at the end of the inline script; leave it in place if the
layout is changed.

## PDFs

Full texts live in a shared Google Drive folder, not in this repo. Drive
permissions control who can open them, and the `PDF in Drive` links fail by
design for anyone without folder access. Never commit publisher PDFs here.

Access is granted to the address we have on record for the weekly calls, and
one approval covers every entry. To use a different address, send a request
and we will add it. A request arriving from an unrecognized address is usually
someone signed in to Google under a second account.

The interlibrary loan scans sit in a subfolder held in Drive's restricted state.
Collaborators can see that the folder exists and nothing more, which is why
those two entries offer no local copy. Anything placed in that subfolder follows
the same rule, so put a scan there when its license does not permit passing it
on.
