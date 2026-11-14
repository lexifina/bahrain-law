# Bahrain: law history in git


The law of Bahrain as a git history: one file per provision, one commit per version on the day it took effect, and the act that made each change as the commit's author. `git blame` names the act behind every article; `git log` lists every change to an article; picking a date gives the text in force that day.

Part of [lexifina/global-law](https://github.com/lexifina/global-law), one git history for every country's law: this is Bahrain's national law, which global-law reads at `bahrain/national/acts/`.

**What is in it now:** the Constitution of the Kingdom of Bahrain as amended, in one version: its preamble and Articles 1 to 125 (126 provisions), as the Legislation and Legal Opinion Commission publishes them in English. Beside it, `legal-system/` holds four files of facts about the state from Wikidata, in two versions; they are not law. No statute, decree-law, regulation or treaty is here yet. [`constitution/README.md`](constitution/README.md) lists every provision; [`REPRODUCE.md`](REPRODUCE.md) says how the files were made.

Each act is a folder with one file per provision: `constitution/art-001.md` is Article 1 and `constitution/preamble.md` the preamble.

The text is in English, the Commission's unofficial translation. The Arabic text, which is the official one and prevails, is not part of this record.

## Questions as git commands

| Question | Command |
| --- | --- |
| Every change to Article 1 of the Constitution | `git log -p --word-diff -- constitution/art-001.md` |
| Which act wrote each line of Article 1? | `git blame constitution/art-001.md` |
| Every version of the Constitution, with the day each took effect | `git log --format="%h %(trailers:key=In-force,valueonly,separator=) %an" -- constitution ":^constitution/README.md"` |
| Article 1 as in force on 1 January 2026 | `python tools/on.py 2026-01-01 constitution art-001` |

**Outside git**, we also host this record publicly, for free:

- **[Ask Claude about Bahraini law](https://global-law.lexifina.com/v1/try_claude?country=bahrain)**: opens Claude with a first question ready.
- **[Ask ChatGPT](https://global-law.lexifina.com/v1/try_chatgpt?country=bahrain)**: the same question in ChatGPT.
- **[Call the API in your browser](https://global-law.lexifina.com/v1/search_law?query=freedom+of+opinion&jurisdictions=bahrain)**: a search of Bahraini law for "freedom of opinion", returned as JSON. See the [documentation here](https://lexifina.com/api/global-law).

Both assistants read the record through the free Global law connector (MCP, `https://global-law.lexifina.com/mcp`); the first time, the chat gives you the link that adds it. Ask in English.

**Host it yourself easily.** All it takes is git and Python, and the tools run on your machine:

```sh
git clone --depth 1 https://github.com/lexifina/global-law && cd global-law
python3 tools/countries.py add bahrain/national/acts
python3 tools/law.py show 2026-01-01 bahrain/national/acts/constitution/art-001.md
```

Opened in Claude Code, Cursor, VS Code or Codex, the clone also starts a local MCP server with the same tools ([MCP.md](https://github.com/lexifina/global-law/blob/main/MCP.md)).

## Dates

Each commit is dated at noon, Asia/Bahrain, on the day the version took effect, and carries it in its `In-force:` trailer:

- the Constitution's one version is dated 25 April 2025, the "Last updated" date of the Commission's page, as the oldest version available. The text is older: notes under 20 of its articles cite the amendments of 2012, 2017 and 2018. A date before 25 April 2025 gives no text;
- the Wikidata facts are dated 14 August 1971, the inception date Wikidata records for the state, and then 30 October 2026, the day they were retrieved, not a day anything was enacted.

No version is credited to a law. The Constitution's version, and the first set of facts, are credited to the publisher, the Legislation and Legal Opinion Commission, as the "oldest version available" (`Kind: publisher`); the later facts to "Wikidata facts as retrieved 2026-10-30". The committer is Lexifina.

## How it is checked

- `tools/check_repo.py` reads every version back from git on the day it took effect and on the day before and compares it with the corpus, whose hash is in `data/corpus.sha256`; it also checks that every commit's trailers parse, that `main` has no merge commits and that no commit is dated in the future.
- `tools/build.py` writes the history from that one corpus file, and the same corpus gives the same commit hashes. [`REPRODUCE.md`](REPRODUCE.md) records that the checks were not yet run for this build and that no second build has been compared.
- The sha256 of the page the Constitution was parsed from is in `data/versions.json`. The page's footnote markers are dropped; its amendment notes are kept below a line at the end of the articles they concern.

## What it does not show

- **Amendment history.** The Commission's page shows one text, so the amendments of 2012, 2017 and 2018 are in it but not as commits of their own, and no earlier text of the Constitution is here.
- **The Arabic text**, which prevails over this English translation.
- **Statutes, decree-laws, regulations and treaties.** None yet, and no catalogue of laws or treaty actions. They will be added only where Law No. 22 of 2006, Article 4(2), clearly covers them.

## Sources

| Source | Kind | Past versions | Notes |
| --- | --- | --- | --- |
| [Legislation and Legal Opinion Commission](https://www.lloc.gov.bh/en/page/The%20Constitution%20of%20the%20Kingdom%20of%20Bahrain) | Official site: the Constitution as amended, in English | no, one text | Page "Last updated 25-April-2025", read on 30 October 2026; marked an unofficial translation, the Arabic text prevails |
| [Wikidata](https://www.wikidata.org/wiki/Q398) | Facts about the state (CC0), not law | as read | Read on 30 October 2026 |

## Licence

See [`LICENSE`](LICENSE). Legislative Decree (Law) No. 22 of 2006, Article 4(2), excludes statutes and all official documents from copyright protection, while the Commission's site terms reserve rights in its content; the text is published only under the Article 4(2) exemption and will be withdrawn on request. The Wikidata facts are CC0 1.0, and so are Lexifina's history, commit messages, tables and tools.

No AI model wrote, translated or corrected legal text; the scripts were written by an AI model (see [`REPRODUCE.md`](REPRODUCE.md)).

## More

From [lexifina/global-law](https://github.com/lexifina/global-law):

- [FEATURES.md](https://github.com/lexifina/global-law/blob/main/FEATURES.md): every feature, and what every corpus must support (`git blame`, `law.py`, the MCP tools)
- [FAQ.md](https://github.com/lexifina/global-law/blob/main/FAQ.md): questions and answers · [CONTRIBUTING.md](https://github.com/lexifina/global-law/blob/main/CONTRIBUTING.md): proposing changes · [MCP.md](https://github.com/lexifina/global-law/blob/main/MCP.md): the MCP server · [REPRODUCE.md](https://github.com/lexifina/global-law/blob/main/REPRODUCE.md): how it was built · [CHANGELOG.md](https://github.com/lexifina/global-law/blob/main/CHANGELOG.md)
- [FRESHNESS.md](https://github.com/lexifina/global-law/blob/main/FRESHNESS.md): how current each corpus is · [Monitoring](https://github.com/lexifina/global-law/tree/main/monitoring): whether updates are running · [WATCHING.md](https://github.com/lexifina/global-law/blob/main/WATCHING.md): how each official source is watched for changes
- [performance/](https://github.com/lexifina/global-law/tree/main/performance): how fast the tools are, measured
- [visualisations/](https://github.com/lexifina/global-law/tree/main/visualisations): charts and bridges across the world's law
- [Vulnerabilities](https://github.com/lexifina/global-law/tree/main/vulnerabilities): mistakes in legislation as published
