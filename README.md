# Data Integration Onboarding (v2)

An interactive onboarding guide for new Data Integration engineers. It walks through the full route of an integration project, from the signed contract to live data, and adapts to each person's background and to the type of data source.

**Live site:** https://raulsteiu.github.io/REPO-NAME/ (replace `REPO-NAME` with this repo's name)

---

## What is new in v2

### Background picker
A dropdown at the top lets each learner choose the background closest to theirs. Every "In ... terms" box, and the Script Agent habit table, then explains things with analogies from that background.

| Option | Used for |
|---|---|
| Plain explanation | No analogy, neutral wording (default) |
| Excel with VBA | Macros, formulas, pivots |
| Excel formulas and pivots (no VBA) | Spreadsheet users |
| SQL / relational databases | Database developers and analysts |
| BI tools | Power BI, Tableau |
| JavaScript / TypeScript | Web and script developers |
| C# / Java | Typed-language developers |
| Python | Data and scripting developers |
| ETL / integration tools | SSIS, Informatica, Talend, SnapLogic, Boomi, Azure Data Factory |
| API / REST / Postman | API-first developers |
| Finance / accounting | Non-coding finance hires |

The SQL "six moves" also show their Excel equivalents for Excel, BI and finance backgrounds.

### Data source picker
Choose **API**, **SQL database**, **SFTP / file**, or **Not sure yet (show all)**. The route adapts:

- The Postman check (phase 3) applies to API sources only. For SQL and SFTP sources it is greyed out on the route map, skipped by the Next and Previous buttons, and left out of the progress count (for example "0 of 6 phases").
- API-only items (Script Agent setup, ClearScript rules, API questions, three script gotchas) are hidden for other sources.
- Ticket rows, setup steps and first-week tasks that depend on the source are shown or hidden to match.
- In "show all" mode, source-specific items carry a small tag (API, SQL, SFTP) so nothing is lost.

Both choices are remembered in the browser.

---

## Existing features

- Seven-phase route map with three lanes (Us, Support, Client) and an exit gate per phase
- Per-phase checklists, deeper reference sections and self-check questions
- Toolbox: DI Studio anatomy, FC vs FPA data (with interactive demo), Script Agent, SQL moves
- Survival kit: gotchas, where to look, and a suggested first-week plan
- Progress saved in the browser (`localStorage`, key `dio_onboarding_v2`), with a reset button
- Responsive layout, keyboard focus states, and reduced-motion support

---

## Project structure

```
.
├── index.html     the whole app (HTML, CSS and JavaScript in one file)
├── .nojekyll      skips Jekyll so GitHub Pages deploys faster
└── README.md      this file
```

No build step, no framework and no external dependencies.

---

## Deploy to GitHub Pages

1. Create a new public repo and upload `index.html`, `.nojekyll` and `README.md`.
2. Go to **Settings > Pages**, set **Source** to **Deploy from a branch**, choose `main` and `/ (root)`, then click **Save**.
3. Wait for the green "pages build and deployment" run in the **Actions** tab, then open the site.

---

## Editing the content

| To change | Where to look in `index.html` |
|---|---|
| Colours and fonts | `:root` variables at the top of the `<style>` block |
| Phase text, checklists, self-checks | `<article class="phase" id="p1">` to `p7` |
| Mark an item as source-specific | Add `data-src="api"`, `"sql"`, `"sftp"` or a space-separated mix (for example `data-src="api sftp"`) to the element |
| Analogies per background | The `ANA` object at the start of the script (keys `p1` to `p7` and `t2`) |
| Script Agent habit table | The `HAB` object in the script |
| Route map cells and source overrides | The `PH` and `OV` arrays in the script |
| Phases skipped for a source | The `SKIP` object in the script |

---

## Good to know

- **Progress is per browser.** It does not sync across devices and the team lead cannot see it.
- **Shared storage on GitHub Pages.** All sites under the same `github.io` account share one browser storage area. This version uses its own key, so it never mixes with other versions.
- **This site is public.** Keep client names, credentials and internal URLs out of the content.
- **This is a summary.** The team documentation holds the current detail and takes precedence.
