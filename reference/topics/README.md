# Topic summaries

Each file here is one topic summary: where the library's evidence stands on one topic. The library shows it at
`/research/topics/<slug>/`, on the systems map and in the corpus map's region panel. The chatbot can read the same
files.

A summary is written for a **topic**, not for a corpus-map region. Regions are recomputed with every release, so their
borders and names change. The map attaches each summary to the region holding most of the records it cites
(`library/src/lib/research/corpus-map.ts`, `SUMMARY_MIN_SHARE`, 40%). A topic that cuts across regions, such as
pharmacogenomics, attaches to each region holding at least 20% of its records, up to three (`SUMMARY_SPAN_SHARE`).

## Format: `<slug>.json`

| Field | What it holds |
|---|---|
| `slug`, `title` | The file name without `.json`, and the topic's name |
| `description` | One sentence, at most 160 characters, no record IDs |
| `system` | Optional: the systems map's key (`library/src/lib/research/systems.ts`) the topic belongs to |
| `written_for`, `written` | The release the summary was written from, and the date (YYYY-MM-DD) |
| `status` | `unreviewed` (published before the curator's review; the first files said `pilot`) or `reviewed` |
| `support` | Optional `true`: the page shows the crisis-line notice near the top (for summaries that discuss suicidality) |
| `in_short` | 3 to 5 bullets, each citing records |
| `shows` | 3 to 6 paragraphs, `{lead, text}`: what the library's evidence shows, most direct first |
| `disagrees` | 2 to 4 paragraphs, `{lead, text}`: counter-evidence, small or uncontrolled studies, findings from one lab |
| `powers` | Optional `{lead, text}`: Dr Powers' view, attributed to him, citing his records |
| `untested`, `tests` | Bullets: what no record has tested, and designs that would test it |

Records are cited as IDs in parentheses at the end of a claim, for example "(PFS-005, DISC-013)". The library links
each one to its record. `npm test` (`tests/topics.test.ts`) checks the following:

- every cited ID is a live record;
- every paragraph cites at least one;
- a retracted record is cited only to say so;
- the Milan cerebrospinal-fluid studies are flagged as possibly sharing patients when cited together;
- each summary still gathers on the map.

## How they're written

Each summary is written from the library's own record pages for one release, and nothing else. Each claim is
cited to a record whose text states it. A second pass checks every citation against the record. The rules:

- Research only. Evidence and mechanisms, never what anyone should take. Treatments appear only as what a study found.
- Every hypothesis is attributed. Dr Powers' views go in `powers`, never in `shows`.
- American spelling, as on the library's editorial pages.

Rewrite a summary for a later release when its region on the map has gained records, and update `written_for` and
`written`.
