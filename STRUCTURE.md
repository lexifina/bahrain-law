# Structure of bahrain-law

Folder names are in Arabic, the language the law is written and searched in. Each legislative instrument is
one file, committed once, dated 12:00 Manama time on the day it took effect. Amendments are their own instruments; the
amended instrument's file names them in its header.

| Folder | What it holds | Path pattern |
| --- | --- | --- |
| `الدستور/` | the Constitution; `الدستور/الترجمة-الإنجليزية/` holds the English translation | `الدستور/art-NNN.md` (Arabic text) |
| `القوانين/` | laws (قانون) | `القوانين/<السنة>/<رقم>.md` |
| `المراسيم-بقوانين/` | decree-laws (مرسوم بقانون) | `المراسيم-بقوانين/<السنة>/<رقم>.md` |
| `الأوامر-الملكية/` | royal and amiri orders (أمر ملكي، أمر أميري) | `الأوامر-الملكية/<السنة>/<رقم>.md` |
| `المراسيم/` | decrees (مرسوم) | `المراسيم/<السنة>/<رقم>.md` |
| `القرارات/` | decisions of the Cabinet, ministers and public bodies | `القرارات/<الجهة>/<السنة>/<رقم>.md` |
| `أحكام-المحكمة-الدستورية/` | judgments of the Constitutional Court | `أحكام-المحكمة-الدستورية/<السنة>/<رقم الدعوى>.md` |
| `الآراء-القانونية/` | legal opinions of the Legislation and Legal Opinion Commission, as it publishes them (heading and principle of each published passage) | `الآراء-القانونية/<السنة>/<رقم الرأي>.md` |
| `legal-system/` | notes on the state and its institutions (English) | |
| `data/`, `tools/`, `visualisations/`, `vulnerabilities/` | tables, scripts and reports about the record | |

`<الجهة>` is the issuer as the title names it (`قرار-وزير-الخارجية`, `قرار-مجلس-الوزراء`).

Instruments about named people (appointments, promotions, transfers, honours, retirements, citizenship) and
announcements are not included.

Every commit carries `Kind:`, `In-force:` and `In-force-basis:` (the clause that sets the day: from issue, from
publication in the Official Gazette, from the day after publication, ...). A text whose in-force day cannot be read
is not committed. Source: the Legislation and Legal Opinion Commission (lloc.gov.bh); legislation is excluded from
copyright by Law No. 22 of 2006, art. 4(2).

Until 2026-11-26 the English Constitution was in `constitution/art-NNN.md`; it was renamed to
`الدستور/الترجمة-الإنجليزية/art-NNN.md` in one commit (`data/paths.json`).

Legal opinions: one file per opinion, one commit, dated by the issue date the Commission prints (`Kind: opinion`).
