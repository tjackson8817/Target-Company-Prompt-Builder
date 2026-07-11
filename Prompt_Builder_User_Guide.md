# Target Company Research Prompt Builder — User Guide

This tool is a single web page (`prompt_builder.html`) that turns a few fields you fill in into a complete, ready-to-send research prompt for Claude. No install, no account, no server — it runs entirely in your browser.

---

## 1. Opening the tool

1. Locate `prompt_builder.html` (wherever your browser saved it — usually your Downloads folder).
2. Double-click it. It opens in your default browser like any web page.
3. If it opens as plain text/code instead of a working page, right-click the file → **Open with** → choose your browser explicitly.

Nothing is sent anywhere when you use this — it's just a form that builds text, entirely on your own machine.

---

## 2. The three "starting point" fields

You only need **one** of these filled in — fill in more than one if you have them, and the tool will combine them.

| Field | What to put in it |
|---|---|
| **Company(s) you know** | A current employer, former employer, competitor — any real company name(s) |
| **Industry / field, plain language** | A description in your own words — no jargon needed (e.g. "commercial HVAC controls") |
| **NAICS code(s), if known** | Skip this if you don't know it — Claude will look it up from the other two fields |

There's also an **Exclude these companies** field (optional) — anything you list there is left out entirely, even if it would otherwise match.

---

## 3. Scope & purpose fields

| Field | What it does |
|---|---|
| **Discovery scope** | **Find new companies** = Claude uses your starting point to go discover additional candidate companies via NAICS codes. **Just enrich these** = Claude only researches the exact company names you typed — no new companies get added. |
| **Companies per code** | Roughly how many companies you want per NAICS code. Leave blank to let Claude use its judgment. 15–30 per code tends to get the best-researched detail; totals above ~50–75 in one prompt tend to come back thinner. |
| **Include secondary/adjacent NAICS codes?** | **Yes** (default) broadens the search to suppliers, vendors, and related-but-differently-classified industries. **No** keeps it tightly scoped to your exact code(s) only. |
| **What is this list for?** | The most important field for personalizing the output — it tells Claude how to judge "Category," "Key Contact," "Opportunity Fit," and "Why This Fits" for every company. Be specific: "job search targets for a Director-level OT cybersecurity role" produces a very different sheet than "prospective customers for our SaaS product." |
| **Preferred location / work arrangement** | Optional. If filled in, an extra column is added to the output rating each company against this preference. |
| **Your background** | Optional. Not a file upload — paste resume, CV, bio, LinkedIn summary, or a few lines of relevant experience directly. No length limit, but a tight paragraph of highlights tends to work better than a full multi-page document — it's easier for Claude to weigh correctly. Sharpens the Suggested Job Title Keywords column and gives Claude something concrete to reason from for Warm Introduction Path (former employers, overlapping experience, relevant credentials) instead of guessing generically. |
| **Include full visual formatting in the tracker?** | **Yes** (default) bakes the full formatting spec into the generated prompt itself — color-coded rating columns, a computed Suggested Priority Rank, clickable Website links, autofilter, frozen panes, zebra striping, and Notes/Summary tabs — so you get the same output in any chat, not just one that happens to already know these conventions. **No** asks for a plain data-only spreadsheet instead. |
| **Add a Job Posting Quick Links tab?** | **Yes** (default) adds a second sheet with one-click LinkedIn Jobs, Indeed, and Google Jobs search links per company, built from the Company and Suggested Job Title Keywords columns using Excel HYPERLINK() formulas — the links stay live and update automatically if you edit either cell later. This generates *search links*, not actual postings data — see Section 12 for the difference and when you'd want real postings instead. |

---

## 4. M&A Research Columns (Optional)

A separate fieldset lets you turn on M&A-specific columns for any list — useful whether you're hunting for acquisition targets or trying to figure out who might want to acquire *you*.

1. Set **Add M&A-specific columns?** to **Yes**. A second option — **M&A angle** — appears.
2. Choose one:
   - **Find acquisition targets** — you're the buyer; the output frames each company as a potential target.
   - **Find likely acquirers** — you want to know who might buy a company like yours; the output frames each company as a potential buyer.
   - **Show fit for either** — rates each company both ways, useful if you're not sure yet which direction you're working.
3. This adds several columns to the output: **Ownership Type** (founder-owned, PE-backed, public, subsidiary), **Recent M&A Activity**, a **Signals** column (worded differently depending on your angle — sale/succession signals vs. acquisition-appetite signals), **Estimated Deal Size Fit**, and an **M&A Role Fit** column that labels each company Likely Acquisition Target / Likely Acquirer / Could Be Either / Unclear.

**Honest limits:** these columns only draw on public information — news, filings, press releases. They won't surface private, undisclosed deal intent (that's what tools like PitchBook exist for), and Claude is instructed not to treat silence as evidence a company isn't open to a deal. Treat this as a research starting point, not a substitute for real diligence.

---

## 5. Reading the Live Prompt Panel

The right-hand panel updates instantly as you type — there's no "Generate" button to click. It always shows the exact prompt you'd get if you copied it right now.

- Click **Copy prompt** (top right of that panel) to copy the whole thing to your clipboard.
- If your browser blocks clipboard access (some do, silently), click **Download .txt** instead — it saves the exact same text as a plain text file you can open and paste from.
- Paste it into a new Claude chat and send it as-is.
- Claude will do the NAICS lookup/expansion (if applicable) and hand you back a downloadable, formatted `.xlsx` tracker.

---

## 6. Saving and reusing templates

If you regularly research the same handful of categories (e.g. "OT Vendors," "Big 4 Consulting," "Utilities"), save yourself the retyping:

1. Fill in the form the way you want it.
2. Type a name in **Template name** (e.g. `OT Vendors`).
3. Click **Save current as template**.
4. Later, pick it from the **Load a saved template** dropdown and click **Load** to instantly refill the form.
5. **Delete** removes a template you no longer need.

Note: templates only persist for as long as the page stays open in your browser tab. If you close or reload the page, saved templates are cleared — they are not written to a file or account. If you want templates that survive between sessions, save your filled-in form values somewhere (like a notes file) and re-paste them.

Try it: fill in the OT vendor names, save as "OT Vendors," fill in something else, save as "Big 4," then flip between them with the dropdown.

---

## 7. How many companies should I actually ask for?

No hard limit — the tool doesn't cap it anywhere. But there's a practical ceiling worth knowing about:

- **Quality vs. quantity tradeoff**: for each company, Claude is actually researching real data (revenue, HQ, leadership, hiring signals, sources) — not just generating rows. Asking for hundreds of companies in one go means either the response runs out of room to do that research properly, or the later rows get thinner/more generic to fit everything in.
- **Rule of thumb**: 15–30 companies per NAICS code tends to get solid, well-sourced research per row. Push much past 50–75 total companies in a single request and you'll likely see accuracy or depth drop off, or the response cut short before finishing the sheet.
- **The "Companies per code" field is just guidance**, not an enforced limit.
- **No limit from Excel itself** — a spreadsheet can hold over a million rows, that's never the bottleneck.
- **For genuinely large-scale research** (hundreds of companies, deep verification on each), Claude's Research/deep-research mode is built for exactly that — it can run many more search passes than a single normal response.

Practically, batch it: run the prompt per NAICS code or per category, and merge results into one tracker, rather than asking for everything at once.

---

## 8. Typical workflow, start to finish

1. Open `prompt_builder.html`.
2. Fill in whatever starting-point info you have.
3. Set your scope, purpose, and (if relevant) M&A angle.
4. Copy the prompt from the right-hand panel.
5. Paste it into a new Claude chat and send it.
6. Download the `.xlsx` tracker Claude produces.
7. Repeat for other categories/NAICS codes, merging results into one master tracker as you go.

---

## 9. Quick troubleshooting

| Problem | Fix |
|---|---|
| The file opens as code/text instead of a page | Right-click → Open with → your browser |
| "Copy prompt" doesn't seem to do anything | Some browsers silently block clipboard access — use **Download .txt** instead |
| Prompt panel just shows placeholder text | You need at least one starting-point field or a purpose filled in |
| Saved templates disappeared | Templates only last for the current browser tab/session — they aren't saved to disk |
| Output rows feel thin/generic | You likely asked for too many companies at once — see Section 7 and batch the request |

---

## 10. What's in the Output Tracker

The prompt asks Claude to research and fill in these columns for every company, one row each:

Company, Website, Industry / Sector, **Industry Emphasized** (the specific niche or market segment a company plays in, not just the broad sector), NAICS Code, NAICS Code Type, Why This NAICS Code, HQ Location / Footprint, Company Size, Revenue Band / Latest Revenue, Growth / Revenue Signal, Hiring Signal, **Recent Hiring Trends** (High/Medium/Low pulled from actual current job postings — LinkedIn Jobs, Indeed, the company's careers page — as of the day the report is run), **Opportunity Relevance** (a general-purpose relevance rating that works whether you're job hunting, prospecting, or scouting M&A targets — no longer tied to one specific industry label), Opportunity Fit, Category, Why This Fits, **Executive Role Fit** (the level most worth targeting at this company — Partner, Managing Director, Practice Lead, VP, Chief Consultant, etc. — based on how the company is actually structured), **Warm Introduction Path** (the most plausible route in — recruiter, executive search, former colleagues, a LinkedIn 2nd-degree connection, conference contacts), Outreach Approach, Key Contacts / Priority Titles, Suggested Search Keywords, **Suggested Job Title Keywords** (job posting search terms, distinct from the people-search terms in Suggested Search Keywords), Source URL, Priority Score, Status, Next Action, and Date Researched. If you turned on M&A columns, five more get added on top of that.

The additions worth knowing about specifically:

- **Industry Emphasized** sits right next to Industry/Sector and adds the market-positioning detail a broad sector label misses — e.g. two companies can both say "Cybersecurity" under Industry/Sector, but one emphasizes OT/industrial security and the other emphasizes cloud-native app security. This column is where that distinction shows up.
- **Hiring Signal** and **Recent Hiring Trends** sit next to each other but measure two different things. **Hiring Signal** is the indirect read — inferred from overall business trajectory: revenue growth, expansion announcements, funding rounds, earnings commentary. **Recent Hiring Trends** is the direct, concrete read — actual current job postings on LinkedIn Jobs, Indeed, or the company's own careers page, as of the day the report runs. A company can score High on one and Low on the other — e.g. strong revenue growth (High Hiring Signal) but a recent hiring freeze (Low Recent Hiring Trends), or vice versa. Because Recent Hiring Trends is a live snapshot, re-run the prompt later for a fresh read rather than trusting an old tracker's number.
- **Opportunity Relevance** replaced an earlier version of this column that baked a specific industry into its own name (like "OT Cybersecurity Relevance"). It's now generic on purpose, so the same tool works cleanly whether your purpose is a job search, sales prospecting, partnership scouting, or anything else — the relevance judgment still happens, it's just not hard-coded to one field.
- **Executive Role Fit** and **Warm Introduction Path** sit next to Why This Fits and are aimed squarely at outreach planning — the first tells you who to target, the second tells you how you're most likely to actually reach them.
- **Suggested Search Keywords** and **Suggested Job Title Keywords** sit next to each other but search for different things. Suggested Search Keywords is for finding *people* — the right person at a company on LinkedIn. Suggested Job Title Keywords is for finding *postings* — 2–4 actual job title variants that specific company would plausibly use, tailored to its Executive Role Fit rather than a generic title (e.g. "VP, Professional Services" for an OT security vendor vs. "Partner, Cyber Security Services" for a Big 4 firm). If you filled in **Your background**, this column also gets sharpened using that context.

## 11. Reading the Formatted Tracker

If you've asked Claude to build the tracker (rather than just generating the prompt), the resulting `.xlsx` comes with formatting built in — not just raw data:

- **Color-coded ratings.** The five rating columns (Growth/Revenue Signal, Hiring Signal, Recent Hiring Trends, Opportunity Relevance, Opportunity Fit) are shaded on a 5-step gradient — green for High, down through yellow-green, yellow, orange, to red for Low (with a slightly darker green for "Very High" where that applies). The color keys off the leading word of the cell, so a cell reading "Medium-High — 149 roles posted..." gets colored for Medium-High. A color legend lives on the **Notes & Assumptions** tab.
- **Suggested Priority Rank (1-25).** A single numeric column sitting right next to the blank Priority Score column. It's a mechanical starting point, not a replacement for your judgment — it weighs Opportunity Fit and Opportunity Relevance heavily (up to 10 points each) and blends the three momentum columns (Growth/Revenue Signal, Hiring Signal, Recent Hiring Trends) as lighter supporting evidence (up to 5 points combined). Hover the column header for a tooltip restating the formula. Use it to get a rough sort order, then compare it against your own Priority Score and overrule it where you disagree — the two columns sit side by side specifically so you can do that comparison at a glance.
- **Website is clickable.** Source URL is left as plain text on purpose — those cells are often citation notes rather than single clean links, so auto-linking them risked producing broken links.
- **Autofilter and frozen panes.** The header row has filter arrows built in, and both the header row and the Company column stay visible while you scroll.
- **Zebra striping** on alternating rows to make it easier to track a row across all the columns.
- **Priority Score, Status, and Next Action** — the three columns meant for you to fill in by hand — get a distinct pale blue fill with a navy left border, so it's visually obvious which columns are Claude's research and which are yours.
- **A Summary tab** with quick counts (companies by Opportunity Fit, by NAICS Code Type, by Category) and a Top 5 by Suggested Priority Rank table, so you don't have to scroll the full sheet to get the gist.

As of this version, all of this is spelled out directly in the generated prompt itself (as long as **Include full visual formatting** is set to Yes, which is the default) — so you get the same formatted output in any chat, not just one that already knows these conventions from earlier context. If you deliberately turned that toggle to **No**, you'll get a plain data-only spreadsheet instead — no colors, no Suggested Priority Rank, no extra tabs.

## 12. The Job Posting Quick Links Tab (and Its Limits)

If **Add a Job Posting Quick Links tab?** is Yes, the tracker gets a second sheet — one row per company, with three `HYPERLINK()` formulas: a LinkedIn Jobs search, an Indeed search, and a Google Jobs search, each built from that company's name and its Suggested Job Title Keywords.

Worth understanding clearly what this is and isn't:

- **It's a search-link generator, not a postings database.** Clicking a link runs a fresh, live search on that site — it doesn't embed actual job postings into your spreadsheet. Open the file six months from now and the links still work; they just show you whatever's posted *then*, not what was posted when the file was built.
- **The links are real formulas, not static text.** Because they're `HYPERLINK()` formulas referencing the Company and Suggested Job Title Keywords cells, if you edit either cell later, the link updates automatically — you don't have to regenerate anything.
- **This is deliberately the cheap, safe option.** Building it costs no extra research — it's pure string templating from data Claude already generated. That's why it defaults to Yes.

**If you actually want real postings** — a table of specific job titles, companies, and URLs, not just search links — that's a different, deliberately separate tool. Live postings data has a much shorter shelf life than company research (postings turn over weekly; company revenue/HQ/size is stable for months), and getting real results means live web search per company on top of the research already happening — so bundling it into this same prompt would either bloat the request or go stale inside the same file as more durable data. Ask about a companion "Job Posting Finder" prompt if you want that — it's built to take a shortlist of companies (ideally your top few by Suggested Priority Rank, not all of them) and their Suggested Job Title Keywords as input, and return actual postings.

## 13. A Faster Way to Fill This Out (reverse note)

If you'd rather not use the web form at all, there's a companion plain-text template — `Target_Company_Research_Prompt_Template` (.md) — with the same fields laid out as fill-in-the-blank text you can paste directly into a Claude chat. Use whichever format is more convenient in the moment; both produce the same result.
