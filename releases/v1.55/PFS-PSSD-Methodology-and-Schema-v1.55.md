# Post-Drug Syndromes Research Library: methodology and schema

Release v1.55. 940 records. Generated from the release, not written by hand.

This document is here so a copy of this release explains itself. The library it describes is at
https://postdrugsyndrome.com/research/ and is archived at https://doi.org/10.5281/zenodo.24142337,
a concept DOI that always resolves to the newest release.

## Citing one record

Records keep their identifier across releases and are never renumbered, so a single record can be
cited as the release DOI plus its id, for example "10.5281/zenodo.24142337, record PFS-005". On the
site the same record is at /research/entries/PFS-005/ (identifiers are upper case in URLs).

**A record's id is `item_id` where it has one, and otherwise derived from the record's own source.**
Glossary terms, timeline events, the mechanism matrix, open questions, gene pages, videos and ICD
groups carry no `item_id`, so they are keyed as below. The claim graph points at these ids, which is
why some of its targets do not appear as an `item_id` anywhere in the file.

| Prefix | Records of this kind | Keyed from |
|---|---|---|
| none | anything with an `item_id` | `item_id` |
| `YT-` | video transcripts | `video_id` |
| `TALK-` | talks and panels | the YouTube id in `url` |
| `GL-` | glossary terms | the term, slugified |
| `TL-` | timeline events | date and event, slugified |
| `MECH-` | mechanism matrix rows | `mechanism_id` |
| `OQ-` | open questions | `question_id` |
| `GENE-` | gene reference cards | `gene_symbol` |
| `PGL-` | Powers gene list | `gene` |
| `ICD-` | ICD code groups | `group_id` |
| `MED-CLASSES` | the medication list | fixed |

## How records entered the library

Each record belongs to exactly one collection, named in its `collection_tag`, so any route can be
browsed or excluded on its own.

**Targeted collection** (`core`, 516 records). Directed searches while the library was first being built gathered peer-reviewed papers, Dr Will Powers’ Reddit posts and YouTube talks, ICD code mappings, medication lists, researcher datasets, and the glossary, timeline, mechanism matrix and open questions.

**Systematic literature sweep** (`literature-sweep-2026-10`, 77 records). The first non-targeted sweep, run on 7 Oct 2026 across five axes: PFS clinical and neurosteroid, PSSD, post-retinoid and other post-drug syndromes, mechanistic pillars, and regulatory and gray literature. Candidates came from web search and the OpenAlex and Crossref APIs; roughly 700 were screened.

**Epigenetics supplement** (`epigenetics-supplement-2026-10`, 15 records). A targeted follow-up the same day to fill the persistence-mechanism gap the first sweep admitted: seven OpenAlex queries, with one duplicate excluded.

**Systems literature review** (`systems-review-2026-10`, 48 records). A targeted review on 9 Oct 2026 of the body systems Dr Powers’ current model implicates: neurosteroid signaling, steroid clearance, the gut–brain axis, hormonal axes, brain clearance, pharmacogenomics, epigenetics and drug-safety history. Candidates came from web search and the OpenAlex and Crossref APIs across five parallel search axes; about 126 were screened and 3 were already in the library. Each peer-reviewed paper kept was confirmed by two independent checks (historical items against primary sources), and every record is tagged with its system and a written justification. The systems map sets out the reasoning.

**Researcher-supplied list** (`researcher-list-2026-10`, 4 records). Papers a researcher reviewing the library flagged as missing, in October 2026. Of the ten on the list, six were already in the library and three identifiers needed correcting; the four new papers were each verified against OpenAlex, Crossref and Europe PMC before joining.

**Curator additions** (`curator-additions`, 136 records). Sources the curator adds one at a time between sweeps, starting October 2026: suggestions sent through the library’s form or the community, items the daily news scout surfaces that belong in the evidence base, and the curator’s own finds. Each record is drafted from the source itself (the paper, abstract or, for talks and panels, a transcript), checked against the library, with any claims the library can’t support marked as such, and approved by the curator before it joins.

**Community curation** (`pssd-discord`, 28 records). The 29-link “Papers & Resources Mentioned” list from the PSSD Discord, each link opened and verified individually. About 40% of the list’s labels did not match the linked content, so every record carries the verified metadata. List item #1 was already in the library and was starred in place.

**SIDEfxHUB cross-check** (`sidefxhub`, 11 records). A cross-check against SIDEfxHUB’s Research & Insights list of articles on post-drug-syndrome research, run on 7 Oct 2026. Every listed paper and interview was opened and verified: 11 were new to the library and joined it here, and the 12 already in it were marked as on the list and starred, each with the title of SIDEfxHUB’s article about it.

**Curator-supplied export** (`powers-reddit-history`, 105 records). A full export of u/drwillpowers’ Reddit history (about 1,737 comments and posts), supplied by the curator, from which items were selected in batches (7 and 9 October 2026), ranked by keyword matches and then reviewed by hand. 79 records come from that export. The 26 others are comments he posted after it, recovered from a public mirror in six batches between 8 and 16 October 2026, as were the posts he was replying to. Where the export’s link pointed at the wrong comment, the record links the corrected location and keeps the original link for reference. The complete export is kept as a private archive; only the curated items are public.

## What a verification status means

284 of 940 records carry one. The rest are
glossary terms and structured rows that describe the library rather than a source, plus records whose
check was never written into the field.

| Status | Records | What it means |
|---|---:|---|
| Verified · Crossref + OpenAlex + PubMed | 3 | Found in all three databases. |
| Verified · Crossref + OpenAlex | 34 | Found in both bibliographic databases. |
| Verified | 139 | Confirmed against the source: bibliographic databases, an official agency page or the publisher’s own page. The record’s note says which. |
| Withdrawn by the publisher | 1 | The source was published and then taken down by its publisher. The record stays so the library's own history is complete, and it must not be used as evidence; the record's note says where the same ground is covered by primary documents. |
| Text recovered via mirror | 105 | Reddit text from the curator’s export, with missing context or post bodies restored from a public mirror in October 2026. |
| Metadata tentative | 1 | The source exists, but some of its details could not be confirmed. |
| Unverifiable · dead link | 1 | Listed by a curator, but the link is dead and its content could not be confirmed. |

## The claim graph

`library_context_cites` maps another record's id to a stance. 2355 links across
476 records. A stance is written by hand as the record's "In the library" note is written, so it
is a judgment, and these are the definitions it should be audited against. Each edge is stored on the
record the note belongs to and reads "the cited record does this to me".

| Stance | Reads as | Links | Meaning | CiTO |
|---|---|---:|---|---|
| `supports` | Supported by | 946 | The cited record reports evidence consistent with this record's claim or mechanism. It does not make the claim certain; it means the two point the same way. | `cito:obtainsSupportFrom` |
| `qualifies` | Qualified by | 537 | The cited record narrows or complicates this record's claim without overturning it: a boundary condition, a subgroup, a dose or duration effect, a shorter-lived result than claimed. | `cito:isQualifiedBy` |
| `contradicts` | Contradicted by | 127 | The cited record reports evidence against this record's claim. Both records stay in the library, and the note says what the disagreement rests on. | `cito:isDisagreedWithBy` |
| `context` | Context from | 745 | The cited record is background, precedent or an adjacent proposal rather than evidence either way: it tells you where the claim sits, not whether it holds. | `cito:obtainsBackgroundFrom` |

The CiTO column maps each stance onto the Citation Typing Ontology (http://purl.org/spar/cito/). The
inverse properties are the correct ones here: an edge records what the *cited* record does to the
record holding it, so `cito:qualifies` would assert the opposite direction.

### A worked example

Record `CROSS-001`, "Enduring sexual dysfunction after treatment with antidepressants, 5α-reductase inhibitors…", carries:

```json
{
  "CUR-030": "supports",
  "CROSS-002": "context",
  "LIT-045": "context",
  "LIT-025": "qualifies",
  "LIT-038": "qualifies",
  "CUR-010": "contradicts"
}
```

Read that as: CUR-030 supported by it; CROSS-002 context from it; LIT-045 context from it; LIT-025 qualified by it; LIT-038 qualified by it; CUR-010 contradicted by it. The prose in `library_context` names each one and says what the link rests on.

## Every field

Counted off this release. A field missing from a record is absent rather than empty.

| Field | Records | Type | Example |
|---|---:|---|---|
| `_source_file` | 940 | string | `"peer_reviewed"` |
| `collection_tag` | 940 | string | `"core"` |
| `item_id` | 505 | string | `"PFS-001"` |
| `library_context` | 476 | string | `"Parts of the review's mechanism have support: SRD5A2 promoter methylation appeared in CSF` |
| `library_context_cites` | 476 | object | `{"DISC-025":"supports","SIDE-009":"supports","LIT-003":"supports","LIT-002":"qualifies","C` |
| `library_context_written` | 476 | string | `"1.29"` |
| `source_type` | 442 | string | `"reddit_post (reposted to forum; original on r/asktransgender)"` |
| `url` | 385 | string | `"https://www.fertstert.org/article/S0015-0282(19)32599-3/fulltext"` |
| `title` | 381 | string | `"Post-finasteride syndrome: a surmountable challenge for clinicians"` |
| `category` | 360 | string | `"neurosteroid"` |
| `authors` | 336 | array, string | `["Traish, Abdulmaged M."]` |
| `relevance` | 328 | string | `"The first human CSF evidence that neuroactive-steroid disruption persists after finasteri` |
| `keywords` | 325 | array | `["neuroactive steroids","cerebrospinal fluid","post-finasteride syndrome","dihydrotestoste` |
| `abstract_or_summary` | 319 | string | `"Using liquid chromatography-tandem mass spectrometry on paired plasma and cerebrospinal f` |
| `journal_or_site` | 308 | string | `"Neuroscience"` |
| `year_or_date` | 308 | string, number | `"2025 (epub 2024 Jun 7)"` |
| `term` | 299 | string | `"Allopregnanolone"` |
| `definition` | 299 | string | `"A progesterone-derived neurosteroid (made via 5-alpha-reductase and 3-alpha-HSD) that pos` |
| `used_in` | 299 | array | `["PFS-004","PFS-005","PFS-011","PFS-012","PSSD-003","DWP-001","DWP-002","MED-001","MED-002` |
| `related_terms` | 299 | array | `["THDOC","Androsterone","Dihydroprogesterone","GABA-A receptor","Brexanolone"]` |
| `doi` | 294 | string | `"10.1016/j.fertnstert.2019.11.030"` |
| `verification_status` | 284 | string | `"verified: OpenAlex + Crossref-indexed + EuropePMC record (title/authors/year/PMID match)"` |
| `references` | 283 | array | `[{"source":"ChEBI","id":"CHEBI:50169","label":"brexanolone","url":"https://www.ebi.ac.uk/c` |
| `study_type` | 251 | string | `"case-control (n=3 patients, n=5 controls)"` |
| `source_note` | 246 | string | `"Added in v1.14 from the curator's glossary (2026-10-10)."` |
| `pmid` | 236 | string | `"23890183"` |
| `fulltext_source` | 195 | string | `"publisher's version (CC BY), University of Milan repository"` |
| `fulltext_url` | 174 | string | `"https://air.unimi.it/bitstream/2434/1027020/2/1-s2.0-S0091302223000626-main.pdf"` |
| `note` | 160 | string | `"Merged in v1.14 with RES-001 (same title, authors, journal and year (J Sex Med 2013)); RE` |
| `starred` | 154 | boolean | `true` |
| `quality_notes` | 150 | string | `"Peer-reviewed review, widely cited, and the clearest single statement of the candidate me` |
| `curated_source` | 145 | string | `"PSSD discord"` |
| `aliases` | 145 | array | `["isoallopregnanolone","sepranolone"]` |
| `curated_note` | 143 | string | `"Already in the library as PSSD-003 (Xie 2026 PSSD review, DOI 10.1177/09246479261468499);` |
| `sample_size` | 143 | string | `"n=300 case reports from 37 countries"` |
| `volume` | 127 | string | `"113(1)"` |
| `date_iso` | 119 | string | `"2019-05-13"` |
| `pages` | 118 | string | `"21-50"` |
| `author` | 117 | string | `"u/drwillpowers (attributed: reposted by propeciahelp user as \"a comment from Dr. Will Po` |
| `subreddit` | 117 | string | `"r/asktransgender"` |
| `corpus_refs` | 111 | array | `["CROSS-001","CROSS-002","medication-lists.md (retinoids)"]` |
| `permalink` | 105 | string | `"https://www.reddit.com/r/DrWillPowers/comments/1wkblxb/the_problems_with_the_theory_of_im` |
| `date_raw` | 105 | string | `"2026-09-20T19:15:54Z"` |
| `parent_context` | 105 | string | `"Powers' comment replies to the original post \"The Problems with the Theory of Impaired A` |
| `oa_status` | 100 | string | `"hybrid"` |
| `sweep_date` | 89 | string | `"2026-10-07"` |
| `axis_id` | 89 | string | `"LIT-A-001"` |
| `sweep_axis` | 89 | string | `"pfs"` |
| `date` | 80 | string | `"circa 2020–2021 (exact date not verified)"` |
| `oa_license` | 74 | string | `"cc-by"` |
| `system_classification` | 71 | string | `"pudendal / peripheral neuropathy"` |
| `pmcid` | 70 | string | `"PMC5302381"` |
| `issue` | 67 | string | `"4"` |
| `explains` | 64 | array | `["SRD5A isoenzymes"]` |
| `type` | 53 | string | `"peer-reviewed review"` |
| `date_precision` | 49 | string | `"month"` |
| `event` | 49 | string | `"Isotretinoin (Accutane) approved by FDA"` |
| `significance` | 49 | string | `"Retinoid whose enduring sexual dysfunction cases later joined the cross-drug syndrome lit` |
| `justification` | 47 | string | `"Dr Powers' current model centers on THDOC/allopregnanolone excess held in place by feedba` |
| `tags` | 45 | array | `["finasteride","5-alpha-reductase-inhibitor","dutasteride","post-finasteride-syndrome","ep` |
| `powers_note` | 45 | string | `"His April 2026 handout lists low allopregnanolone despite normal progesterone and pregnen` |
| `plain` | 43 | object | `{"summary":"Researchers in Italy measured steroid hormones that act on the brain in the sp` |
| `evidence` | 43 | object | `{"design":"Case-control pilot: neuroactive steroids in paired cerebrospinal fluid (CSF) an` |
| `status` | 37 | string | `"duplicate-tombstone"` |
| `year` | 29 | number | `2020` |
| `confidence` | 29 | string | `"direct"` |
| `journal` | 28 | string | `"Fertility and Sterility"` |
| `citation` | 28 | string | `"Traish AM. Post-finasteride syndrome: a surmountable challenge for clinicians. Fertil Ste` |
| `gene_symbol` | 28 | string | `"AKR1C1"` |
| `full_name` | 28 | string | `"aldo-keto reductase family 1 member C1"` |
| `location` | 28 | string | `"10p15-p14 (AKR1C gene cluster, chromosome 10)"` |
| `function_summary` | 28 | string | `"Cytosolic NAD(P)H-dependent oxidoreductase with mainly 20-alpha-hydroxysteroid dehydrogen` |
| `corpus_relevance` | 28 | string | `"Member of the AKR1C family at the center of Powers' original PFS theory (DWP-001), which ` |
| `evidence_tier` | 28 | string | `"theoretical-per-Powers"` |
| `related_genes` | 28 | array | `["AKR1C2","AKR1C3","AKR1C4","SRD5A1","SRD5A2"]` |
| `name` | 26 | string | `"PFS Network"` |
| `mechanism` | 25 | string | `"Inhibits type II (and at 5 mg also type I/III) 5-alpha-reductase, blocking testosterone-t` |
| `sidefxhub_article_title` | 23 | string | `"PFS and PSSD: similar symptoms, a possible link"` |
| `speculation_flag` | 22 | boolean | `true` |
| `score` | 22 | number, string | `32` |
| `fulltext_note` | 19 | string | `"Link updated 2026-10-09: IOS Press journals moved to SAGE"` |
| `gene` | 17 | string | `"UGT2B17"` |
| `variant` | 17 | string | `"defective (major)"` |
| `duplicate_of` | 15 | string | `"SIDE-009"` |
| `tombstone_note` | 15 | string | `"Merged in v1.35 into SIDE-009, the published paper of the Baylor gene-expression study (H` |
| `ncbi_gene_id` | 15 | number | `6715` |
| `source_url` | 15 | string | `"https://www.reddit.com/r/DrWillPowers/comments/1poj0ky/i_think_i_have_figured_out_at_leas` |
| `proposed_collection_tag` | 15 | string | `"epigenetics-supplement-2026-10"` |
| `data_type` | 14 | string | `"patient advocacy org; research funder; science-summaries hub"` |
| `access` | 14 | string | `"public website; research updates via mailing list"` |
| `source_post` | 14 | string | `"I think I have figured out at least one specific phenotype of PFS, and it is different fr` |
| `thread_title` | 14 | string | `"Theory as to why some people so sensitive to Calcium-D-Glucarate"` |
| `thread_author` | 14 | string | `"[username removed]"` |
| `sidefxhub_article_url` | 13 | string | `"https://sidefxhub.com/articles/scientific-research/exploring-androgen-receptor-gene-polym` |
| `mirror_url` | 13 | string | `"https://r.genit.al/r/DrWillPowers/comments/1wgdfut/why_x_treatment_crashed_me_bro_is/"` |
| `generic` | 13 | string | `"finasteride"` |
| `brands` | 13 | array | `["Propecia (1 mg, androgenic alopecia)","Proscar (5 mg, BPH)"]` |
| `drug_class` | 13 | string | `"5-alpha reductase inhibitor (5-ARI)"` |
| `syndromes` | 13 | array | `["PFS"]` |
| `corpus_citations` | 13 | array | `["PFS-001","PFS-002","PFS-004","PFS-005","PFS-006","PFS-007","PFS-009","PFS-010","PFS-011"` |
| `label_notes` | 13 | string | `"FDA (April 2012): labels of finasteride 1 mg and 5 mg revised to indicate sexual side eff` |
| `sidefxhub_curated` | 12 | boolean | `true` |
| `mechanism_id` | 12 | string | `"MECH-01"` |
| `pfs_status` | 12 | string | `"supported"` |
| `pfs_evidence` | 12 | string | `"CSF LC-MS/MS in PFS patients shows persistently decreased tetrahydroprogesterone, isopreg` |
| `pssd_status` | 12 | string | `"suggested"` |
| `pssd_evidence` | 12 | string | `"Xie 2026 review identifies allopregnanolone depletion via 5α-reductase inhibition as a PS` |
| `prsd_status` | 12 | string | `"unstudied"` |
| `prsd_evidence` | 12 | string | `"No evidence in the library on isotretinoin and neurosteroids."` |
| `evidence_notes` | 12 | string | `"The most directly studied PFS mechanism in the library: three small CSF studies from one ` |
| `ncbi_url` | 12 | string | `"https://www.ncbi.nlm.nih.gov/gene?LinkName=geoprofiles_gene&from_uid=131962649"` |
| `permalink_export_verbatim` | 12 | string | `"https://www.reddit.com/r/DrWillPowers/comments/1sg3yin/if_you_have_pfs_do_not_panic_if_yo` |
| `target` | 12 | string | `"Bacterial beta-glucuronidase in the gut lumen"` |
| `proposed_mechanism` | 12 | string | `"Conjugated steroids are secreted into the gut, where bacterial beta-glucuronidase can dec` |
| `mechanism_strength` | 12 | string | `"in-vitro"` |
| `mechanism_refs` | 12 | array | `["CUR-127","MECH-018"]` |
| `human_evidence` | 12 | string | `"None for androgen handling. The reactivation step the rationale depends on is now measure` |
| `human_evidence_class` | 12 | string | `"none"` |
| `human_evidence_refs` | 12 | array | `["CUR-127","MECH-018","CUR-099"]` |
| `population_evidence` | 12 | string | `"None. No study in PFS, PSSD or PRSD has given calcium D-glucarate and measured anything."` |
| `population_evidence_class` | 12 | string | `"none"` |
| `population_evidence_refs` | 12 | array | `[]` |
| `reported_use` | 12 | string | `"Powers describes it in his protocol, paired with indomethacin, as support for glucuronida` |
| `reported_use_scale` | 12 | string | `"unquantified"` |
| `reported_outcome` | 12 | string | `"mixed"` |
| `reported_use_refs` | 12 | array | `["DWP-002","PRH-0178","PRH-1546","PRH-0051","PRH-0052","PRH-1535","PRH-1536","PRH-1537"]` |
| `reported_use_private` | 12 | boolean | `false` |
| `risks` | 12 | string | `"Sold as a supplement, so neither dose nor purity is standardized. Beta-glucuronidase inhi` |
| `counter_signals` | 12 | array | `["CUR-099"]` |
| `research_question` | 12 | string | `"Does calcium D-glucarate change urinary or serum androgen glucuronide concentrations in p` |
| `study_design_needed` | 12 | string | `"A small open-label crossover in symptomatic patients, measuring conjugated and unconjugat` |
| `measurable` | 12 | string | `"Serum and urinary testosterone, DHT and androsterone glucuronides; fecal beta-glucuronida` |
| `not_a_recommendation` | 12 | boolean | `true` |
| `curator_note` | 12 | string | `"The most discussed intervention in the library and the one with the clearest measurement ` |
| `channel` | 11 | string | `"SIDEfxHUB: PFS & PSSD Patient Organisation"` |
| `transcript_status` | 11 | string | `"full (YouTube auto-generated English captions, 350 cues)"` |
| `uniprot_id` | 11 | string | `"ANDR_HUMAN"` |
| `crosscheck_source` | 11 | string | `"SIDEfxHUB research-and-insights (2026-10-07)"` |
| `maintainer` | 10 | string | `"PFS Network (charity launched on Rare Disease Day 2021 by propeciahelp.com organizers)"` |
| `question_id` | 10 | string | `"OQ-001"` |
| `question` | 10 | string | `"Are persistent symptoms driven by neurosteroid deficiency or neurosteroid excess?"` |
| `side_a` | 10 | string | `"Deficiency model"` |
| `side_b` | 10 | string | `"Excess model"` |
| `evidence_needed` | 10 | string | `"Direct measurement of neurosteroid concentrations in CSF of symptomatic vs recovered vs n` |
| `upload_date` | 9 | string | `"2026-04-29"` |
| `duration` | 9 | string | `"21:27 (1287s)"` |
| `also_listed_in` | 8 | array | `["researcher-list-2026-10"]` |
| `required_reading` | 8 | string | `"Cerebrospinal fluid studies"` |
| `video_id` | 8 | string | `"iWFDBRTgT3g"` |
| `speaker` | 8 | string, array | `"Dr. Will Powers (interviewee); Robb, SIDEfxHUB (interviewer)"` |
| `verified_live` | 8 | string | `"2026-10-07"` |
| `summary` | 8 | string | `"In this interview, recorded at the 2026 PFS/PAS/PSSD summit, Dr Powers sets out his unify` |
| `date_tabled` | 8 | string | `"2026-09-14"` |
| `views_at_collection` | 7 | number | `9032` |
| `format` | 7 | string | `"interview"` |
| `transcript_file` | 7 | string | `"transcripts/iWFDBRTgT3g.srt"` |
| `group_id` | 6 | string | `"ICD-SEX-01"` |
| `group_name` | 6 | string | `"Core sexual dysfunction (Healy 2022 necessary/additional criteria)"` |
| `maps_to` | 6 | array | `["CROSS-002 (Healy 2022): necessary criterion (2) enduring change in genital sensation; ad` |
| `codes` | 6 | array | `[{"icd10cm":"F52.0","icd10cm_desc":"Hypoactive sexual desire disorder","icd11":"HA00","icd` |
| `article` | 5 | string | `"101114"` |
| `language` | 5 | string | `"Dutch"` |
| `channel_note` | 3 | string | `"Clip from the SIDEfxHUB summit interview (iWFDBRTgT3g); published by Moral Medicine, cred` |
| `source` | 3 | string | `"Dr. Will Powers Interview [PFS / PAS / PSSD Summit 2026], SIDEfxHUB"` |
| `key_points` | 3 | array | `["[00:00:00] Opens with a disclaimer: not a doctor, not medical advice; consult a physicia` |
| `repost_url` | 2 | string | `"https://forum.propeciahelp.com/t/dr-will-powers-theory-on-pfs/44137/1"` |
| `established` | 2 | number, string | `2021` |
| `view_count` | 2 | number | `8086` |
| `transcript_files` | 2 | array | `["transcripts/mQAnwC6dTkE.srt","transcripts/mQAnwC6dTkE.txt"]` |
| `discord_list_ref` | 2 | string | `"#17: listed as 'Game Over Post Finasteride Syndrome' (2024); actual upload 2023-02-20"` |
| `curated_list_item` | 1 | number | `1` |
| `verification_note` | 1 | string | `"Speaker not confirmed as Powers (topically aligned with his neurosteroid framing); label ` |
| `availability` | 1 | string | `"Unavailable: video removed or made private (yt-dlp: 'This video is unavailable')"` |
| `gap_note` | 1 | string | `"The library previously described it as a TRT-clinic clip asserting CSF 5α-reductase produ` |
| `dataset` | 1 | string | `"PFS-PSSD-Post-Drug-Syndromes-Medication-Lists"` |
| `version` | 1 | number | `1` |
| `created` | 1 | string | `"2026-10-07"` |
| `source_corpus` | 1 | string | `"~/workspace/pfs_pssd_corpus/peer_reviewed_literature.md"` |
| `classes` | 1 | array | `[{"id":"5ARI","name":"5-alpha reductase inhibitors","mechanism_class":"Block conversion of` |
| `label_notes_ema_2019` | 1 | string | `"EMA PRAC (May 2019): product information for SSRIs/SNRIs amended with the sentence 'There` |
| `forum_url` | 1 | string | `"https://forum.propeciahelp.com/latest"` |
| `pssd_page` | 1 | string | `"https://rxisk.org/post-ssri-sexual-dysfunction-pssd/"` |
| `contact` | 1 | string | `"robb@sidefxhub.com"` |
| `retraction` | 1 | string | `"RETRACTED: Drug Metab Dispos. 2018 Sep;46(9):1360. Do not cite as evidence."` |
| `event_name` | 1 | string | `"MAHA Institute, Mental Health and Overmedicalization Summit (opening \"lived experience\"` |
| `claims_flagged` | 1 | array | `[{"claim":"Sexual side effects affect 50-70% of SSRI users","by":"Lauren Friedman","librar` |
| `title_english` | 1 | string | `"Persistent sexual dysfunction: antidepressants, finasteride and retinoids"` |
| `target_genes` | 1 | array | `["UGT2B17","UGT2B7","UGT1A1"]` |

## Limits

Summaries are paraphrases written for research use; verify against the originals. Statements by named
clinicians are their own hypotheses, attributed as such. Patient accounts are uncontrolled self-reports.
Nothing here is a diagnosis, a treatment recommendation or dosing guidance.
