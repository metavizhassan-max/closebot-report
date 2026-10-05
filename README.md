# Closebot Issues Investigation — We Build Trades (Daniel Brown)

Purpose: investigate client-reported bot issues over the last ~2–3 weeks, evidence them
with real data from Closebot + GoHighLevel, find root causes, and assemble an internal
document for Daniel.

## How this folder is organised

| Path | What it holds |
|------|----------------|
| `README.md` | This file — the system + procedure |
| `ISSUES_LOG.md` | Master index: one row per client issue, status, root cause |
| `clients/_TEMPLATE.md` | Template copied for each client investigation |
| `clients/<business>.md` | One file per client: issue, problem lead, good lead, cause, fix |
| `data/` | Cached raw data (bots, personas, sources, agency summary) |
| `bots_report.csv` | All 270 bots → source + persona |
| `personas_report.csv` | All 253 personas → job flows + sources |

## Investigation procedure (per client)

1. **Input from Hassan:** business name, issue link (hq.webuildtrades.com / Trello),
   the issue text, and the GHL sub-account PIT token.
2. **Identify the bot:** map business → Closebot source → bot + persona + version
   (using `bots_report.csv` / `data/`).
3. **Pull the problem lead** from GHL (conversation where the bot failed).
4. **Pull a clean lead** from GHL (conversation that went correctly) for comparison.
5. **Diagnose:** what the bot did wrong, and why (prompt/persona, config, AI-off,
   model behaviour, recent bot edit, source data).
6. **Record** in `clients/<business>.md` and add a row to `ISSUES_LOG.md`.

## Security rules

- **Never store secrets in this folder.** GHL PIT tokens and access tokens are used
  only in-session and are NOT written to any file.
- Raw source export from Closebot carried GHL access tokens; it was sanitised to
  `data/sources.json` (ids/names only) and the token-bearing copy deleted.
- Contact PII (names, phones, emails) is minimised in stored notes — use lead IDs
  and describe behaviour rather than copying personal data unless needed as evidence.

## Baseline (from Closebot agency summary)

- Messages: last month **3,148** → this month **800**
- Bookings: last month **131** → this month **31**
- Active sources: last month **86** → this month **71**
- Total leads in system: **52,115**

These point to a real drop in the investigation window — to be explained by the issues.
