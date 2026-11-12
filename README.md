# Post-Drug Syndromes Research Library: release files

The versioned data releases behind
**[postdrugsyndrome.com/research](https://postdrugsyndrome.com/research/)**, an open research library on
post-finasteride syndrome (PFS), post-SSRI sexual dysfunction (PSSD) and post-retinoid syndrome.

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24142337.svg)](https://doi.org/10.5281/zenodo.24142337)

Browse the library itself at [postdrugsyndrome.com/research](https://postdrugsyndrome.com/research/), where
every record is cross-linked, searchable and readable in context. This repository holds the machine-readable
releases those pages are built from.

## What a release contains

`releases/v1.56/` is the current release. Each one holds five files:

| File | What it is |
|---|---|
| `PFS-PSSD-Corpus-v1.56.json` | every record, with full structure |
| `PFS-PSSD-Corpus-v1.56.csv` | the same records, flattened, one row each |
| `PFS-PSSD-Post-Drug-Syndromes-Corpus-v1.56.md` | a readable edition |
| `PFS-PSSD-Corpus-v1.56-changes.json` | what changed since the previous release |
| `PFS-PSSD-Methodology-and-Schema-v1.56.md` | **read this first** |

**Start with the methodology and schema document.** It is generated from the release itself, so it cannot
drift from what the files hold. It covers the nine routes records entered the library by, what each
verification status means, the claim graph and its four stances, all 188 fields with how many records carry
each, and how to cite a single record.

v1.56 holds **940 records**: peer-reviewed papers, preprints and conference abstracts, regulatory documents,
attributed clinician commentary, videos and transcripts, patient-authored accounts, a 299-term glossary, a
49-event timeline, a mechanism matrix rated separately for each syndrome, a body-systems review, medication
and ICD-code tables, dataset and registry listings, and a list of open questions.

## The claim graph

The part that makes this a library rather than a bibliography is `library_context_cites`: **2,355
hand-written links across 476 records**, each saying how one record bears on another.

| Stance | Links | Means |
|---|---:|---|
| `supports` | 946 | reports evidence consistent with the claim |
| `context` | 745 | background or precedent, not evidence either way |
| `qualifies` | 537 | narrows or complicates the claim without overturning it |
| `contradicts` | 127 | reports evidence against the claim |

Each is a judgment written as a record's "In the library" note is written, which is why the definitions are
published with every release and mapped onto the
[Citation Typing Ontology](http://purl.org/spar/cito/) so other tools can read them.

## The reference data

`reference/` holds material the site renders that the release files do not carry: 577 per-gene reference
pages, the 10 topic summaries, the primer, and `related.json`, a similarity index built from record
embeddings. These track the site rather than a frozen version, so they are not part of a release or of the
Zenodo deposit. The gene pages quote UniProt (CC BY 4.0) and NCBI Gene, attributed on each page.

## Citing a release

Releases are immutable and versioned. Cite the one you used:

> Taverna, J. (2026). *Post-Drug Syndromes Research Library: a curated corpus on PFS, PSSD and post-retinoid
> syndrome (v1.56)* (Version 1.56) [Dataset]. Zenodo. https://doi.org/10.5281/zenodo.24171923

`10.5281/zenodo.24142337` is the concept DOI and always resolves to the newest release, so cite it when the
version does not matter. Records keep their identifier across releases, so a single record can be cited as
the DOI plus its id, for example "10.5281/zenodo.24142337, record PFS-005".

Every release is archived on [Zenodo](https://doi.org/10.5281/zenodo.24142337) permanently. This repository
tracks recent releases; Zenodo is the archive of record.

## Usernames in the community records

Some records quote public forum threads. **Private individuals' usernames are replaced with
`[username removed]`.** Dr Will Powers' own handle is kept, because his commentary is attributed to him
throughout the library. Permalinks still resolve to the original threads, which carry their authors.

## License

The library's own writing and structure is **CC BY 4.0**. The papers and documents it describes, short
verbatim quotations kept as context, and material by named third parties remain with their authors. See
[LICENSE](LICENSE) for what each part covers.

## Not medical advice

Nothing here is a diagnosis, a treatment recommendation or dosing guidance. Statements by named clinicians
are their own hypotheses, attributed as such. Patient accounts are uncontrolled self-reports.

## Corrections

Found an error in a record, or a source that belongs in the library?
[Open an issue](../../issues), or use the
[suggestion form](https://postdrugsyndrome.com/research/submit/) on the site.
