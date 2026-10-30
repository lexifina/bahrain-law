# How this repository was made (Bahrain)

This file is written by the build on 2026-10-30, the day the source data was retrieved.

## Sources

| Source | Address | Retrieved | Licence |
| --- | --- | --- | --- |
| Legislation and Legal Opinion Commission: The Constitution of the Kingdom of Bahrain (English) | <https://www.lloc.gov.bh/en/page/The%20Constitution%20of%20the%20Kingdom%20of%20Bahrain> | 2026-10-30 | Law No. 22 of 2006 Art. 4(2) excludes statutes and official documents from copyright; the site terms (lloc.gov.bh/en/page/Terms-and-Conditions) reserve rights in site content. Both recorded in LICENSE. |
| Wikidata | <https://www.wikidata.org/wiki/Q398> | 2026-10-30 | CC0 1.0 |

Every word of law in this repository comes from these sources. Lexifina reads them and records each act's dated versions, and the laws that made each change, in one corpus file. This repository is built from that file.

## What is in it

| Act | Title | Versions | Span |
| --- | --- | ---: | --- |
| `constitution` | The Constitution of the Kingdom of Bahrain (as amended) | 1 | 2025-04-25 to 2025-04-25 |
| `legal-system` | Bahrain: legal system facts (Wikidata) | 2 | 1971-08-14 to 2026-10-30 |

The build made 3 commits:

| Commits | Kind |
| ---: | --- |
| 2 | first version of an act |
| 1 | one law on its in-force day |
| 0 | changes no amendment note explains, credited to the publisher |

Other counts:
- 0 commits on the branch `future`: laws not yet in force on 2026-10-30.
- 0 commits dated 1 January 1970: in force before 1970, with the real day in their `In-force` trailer.
- 1 laws in the record.
- 4 tags.

## Dates

Each commit is dated at noon (Asia/Bahrain) on the day the change took effect. The other dates, enacted and published, are trailers.

When a law gives no date of its own, the default rule applies: The constitution is the amended text the Commission publishes; its in-force date is the page's "Last updated" date, as the oldest version available. The amended Constitution took effect on publication in the Official Gazette (final clause). https://www.lloc.gov.bh/en/page/The%20Constitution%20of%20the%20Kingdom%20of%20Bahrain

## How the history is built

`tools/build.py` turns the corpus into this history in one pass: one commit per law, on the day it took effect. The same corpus always gives the same commit hashes. `tools/check_repo.py` reads every version back from git and compares it with the corpus. `tools/on.py` shows the law as it stood on any date. The corpus format is described in `tools/SCHEMA.md`.

- Corpus: sha256 `7b8121b0598a9e799abe97b8e17e6ac2f50f1eef563bf9c1038af0253acda3ff` (89912 bytes).
- Builder blob hashes (`git hash-object`): `build.py` `a4faa25af85facb64b956b372f6b528aafdd7ec1`, `check.py` `3e59cb6f05eccb94a9ec14431a7f6781221e83ef`, `on.py` `644a6c0857fbcc72562032b58d57aa113fee0641`.
- Python 3.12.10; git version 2.46.0.windows.1.

## Checks

Not yet run for this build.

No second build of this corpus has been compared yet.

## Decisions made by hand

- English is built: the Commission's English page of the Constitution as amended (every Article 1-125 and the preamble). The Commission labels it an unofficial translation; Arabic prevails.
- The page is dated by its own "Last updated 25-April-2025"; it is the oldest version available, credited to the publisher (no past versions are online).
- Legal basis for reuse: Law No. 22 of 2006 Art. 4(2) excludes statutes and official documents from protection; the site terms reserve the content. Both are quoted in LICENSE. Law text is published only under that exemption.
- The Law No. 22 of 2006 English text on bahrain.bh is an Economic Development Board unofficial translation and was not republished.
- Wikidata facts (CC0) form the "legal-system" act: one version at the inception date Wikidata records (1971-08-14), one at the retrieval date 2026-10-30.
- Not built: law catalogue and treaty actions (no open index could be read inside the time box;

## What AI did and did not do

The scripts that read the sources and build this repository were written by Claude Code running Claude Opus 5.5 (`claude-opus-5-5`) under Lexifina's direction.

No model wrote, translated or corrected legal text. No model runs at build time. Every word of law in this repository comes from the official sources above.

The commit messages are written by `build.py` from the source data.

Model use at data-build time:
- Claude Code with Claude Sonnet 5.5 wrote Lexifina's code and chose the sources; it did not write or alter any legal text. The code is deterministic and runs no model.
