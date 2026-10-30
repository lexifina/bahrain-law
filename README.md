# Bahrain: law history in git

The law of Bahrain as a git history: one file per provision, one commit per law on the day it took effect, and the law that made each change as the commit's author. `git blame` names the law behind every paragraph; `git log` lists every change; picking a date gives the text in force that day.

It follows the shared design of [lexifina/global-law](https://github.com/lexifina/global-law).

## What this repository holds

A first build, not complete. It holds the Constitution of Bahrain as amended (preamble and Articles 1 to 125, in English) and a small set of Wikidata facts about the legal system. **No other law text is published**, and the catalogue of laws and treaty actions is not built yet. Bahrain's other laws are on the Commission's site under terms that reserve rights; they will be added only where Law No. 22 of 2006, Article 4(2) clearly covers them.

| Folder | Act | Versions | History |
| --- | --- | ---: | --- |
| `constitution/` | The Constitution of the Kingdom of Bahrain, as amended (English) | 1 | One version: the Legislation and Legal Opinion Commission's page "Last updated 25 April 2025". No earlier versions are online. |
| `legal-system/` | Legal system facts from Wikidata (CC0) | 2 | The state's inception (14 August 1971), then the facts Wikidata held on 30 October 2026. |

## Source

The English text of the Constitution is copied from the [Legislation and Legal Opinion Commission](https://www.lloc.gov.bh/en/page/The%20Constitution%20of%20the%20Kingdom%20of%20Bahrain) of the Kingdom of Bahrain. The Commission labels the English an unofficial translation: **the Arabic text prevails**. The official language is Arabic; this build is in English only. The Wikidata facts are from [Wikidata](https://www.wikidata.org/wiki/Q398) (CC0).

## Dates

Each file is dated by the day it took effect. The Constitution has no earlier version online, so its single commit is "oldest version available", dated by the page's own "Last updated: 25-April-2025" and credited to the Commission. The Wikidata facts are dated by the inception date Wikidata records (14 August 1971), then by the retrieval date (30 October 2026).

## How it is checked

Every version is read back from git on the day it took effect and on the day before (`tools/check_repo.py`) and must match `corpus.json`; results are in `REPRODUCE.md`.

## What "author" means

The author of a commit is the law (or, for facts, the retrieval) that made the change, with an e-mail address that cannot exist (`<law key>@lloc.gov.bh.invalid`). The committer is always Lexifina.

## Limits

Only the single current text is held, so there is no amendment history. The English is the Commission's unofficial translation. Footnote markers on the page are dropped.
