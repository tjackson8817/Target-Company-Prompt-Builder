# Target Company Research Prompt Builder — User Guide

This tool is a single web page (`prompt_builder.html`) that turns a few fields you fill in into a complete, ready-to-send research prompt for Claude. No install, no account, no server — it runs entirely in your browser.

---

## Claude Settings You'll Need Before You Start

This prompt asks Claude to do two things: research live, and build a real `.xlsx` file. Both depend on a setting that isn't always on by default — if either is off, Claude will tell you so directly (and honestly) rather than fake the result, but it's faster to just check both up front.

| Setting | Why you need it | Where to find it |
|---|---|---|
| **Web search** | Without it, Claude can't do the actual live company research this tool depends on — it would only be able to answer from training data, which goes stale and can't tell you what a company's revenue or hiring activity looks like today. | Click the **+** (or slider) icon in the chat input, find **Web search**, toggle it on. On Team/Enterprise accounts, an admin has to enable it workspace-wide first before individual members can turn it on. |
| **Code execution and file creation** | This is what lets Claude actually build and hand you a downloadable `.xlsx` — without it, Claude can still do the research and present it as a table in the chat, but it has no way to package that into a real file. | **Settings → Capabilities**, toggle **Code execution and file creation** on. |

If you ever get a response back that reads like a polite explanation of a missing tool instead of your tracker, this is almost always why — check both toggles and re-run.

---

## 1. Opening the tool

1. Locate `prompt_builder.html` (wherever your browser saved it — usually your Downloads folder).
2. Double-click it. It opens in your default browser like any web page.
3. If it opens as plain text/code instead of a working page, right-click the file → **Open with** → choose your browser explicitly.

Nothing is sent anywhere when you use this — it's just a form that builds text, entirely on your own machine.

---

## 2. The three "starting point" fields

You only need **one** of these filled in — fill in more than one if you have them, and the tool will combine them.

**What's a NAICS code, and why does it matter here?** NAICS (North American Industry Classification System) is the standard system the U.S. and Canadian governments use to categorize every industry — most real companies fall under one or more of these codes. They matter for this tool specifically because they're what makes company discovery *systematic* rather than a guess: instead of Claude just listing "companies I've heard of" in your space, a code defines the actual, complete category a company belongs to — including the smaller, less-visible players a plain keyword search would miss. This is why the tool can build a genuinely comprehensive target list, not just a list of the most famous names. You don't need to know your code going in — the Industry/field description below is enough for Claude to look it up.

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
| **Add a Job Posting Quick Links tab?** | **Yes** (default) adds a second sheet with one-click LinkedIn Jobs, Indeed, and Google Jobs search links per company, built from the Company and Suggested Job Title Keywords columns using Excel HYPERLINK() formulas — the links stay live and update automatically if you edit either cell later. This generates *search links*, not actual postings data — see Section 13 for the difference and when you'd want real postings instead. |
| **Add a Job Post Finder tab?** | **Yes** (default) adds a third, minimal sheet — Company Name in column A, the full Suggested Job Title Keywords cell in column B, one row per company. No formulas, no links — plain data meant for you to copy a company and its keyword variants and paste them into whatever job board or search tool you want to check by hand. See Section 14 for how this differs from the Quick Links tab above it. |
| **Add an Industry Events & Forums tab?** | **Yes** (default) adds a tab of real, upcoming conferences and trade shows relevant to your stated industry/purpose — one row per event, not per company. Also lets you set how far ahead to look: next 6 months, next 12 months (default), or any upcoming date. See Section 15 for how this connects to your Category column. |
| **Add a Company Activity & Events tab?** | **No** by default (this is a harder research task than the two tabs above it). One row per *company* instead of per event — recent LinkedIn activity, podcast/webcast appearances, and upcoming events that company is attending or speaking at. See Section 16 — coverage is expected to be uneven, and Claude is told to say "No recent public activity found" rather than invent something. |
| **Compensation Benchmark** *(not a toggle — always included alongside the 10-K contact check)* | For publicly traded companies, if the named 10-K contact also appears as a Named Executive Officer in the company's proxy statement, reports their disclosed total compensation. See Section 18 for why this will only fire for a minority of companies. |
| **Full research is capped at 25 companies** *(not a toggle — fixed)* | Named companies plus any NAICS-discovered candidates, combined. If your total exceeds 25, Claude runs a quick qualification pass, gives full research to the strongest 25, and puts everyone else in a lighter Tier 2 list. See Section 8 for the full mechanism. |
| **Include large diversified players in Tier 2?** | **No** (default) keeps Tier 2 focused on genuine specialists in your stated industry. **Yes** includes large, diversified companies where your industry is one product line among many — kept in their own clearly labeled block, not blended with the focused list. Only matters if Tier 2 gets used. See Section 8. |

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

As of this version, this has a real answer instead of "it depends": **full research is capped at 25 companies, always.** This isn't a soft suggestion — it's built into the generated prompt itself, for two reasons: past 25, Claude is doing genuinely deep research (revenue, hiring signals, 10-K checks, sources) on each one, and quality/completeness suffers past that point regardless of how the request is worded; and 25 is also what keeps the output a clean fit for the other tools in this suite (Job Posting Finder, LinkedIn Contact Enrichment, Outreach Message Builder), which are all tuned around batches of 25 or fewer.

What happens if your named companies plus any NAICS-discovered candidates add up to more than 25 total is covered in full in Section 8 — short version: you still get a complete, usable result, just split across two tiers of depth rather than thinned out evenly across everyone.

A few things that don't change:

- **No limit from Excel itself** — a spreadsheet can hold over a million rows, that's never the bottleneck.
- **The "Companies per code" field now governs the candidate *pool*** feeding into the 25-cap, not a count that all get full research automatically — see Section 3.
- **For research needs genuinely beyond what this tool is built for** (hundreds of companies, deep verification on all of them), Claude's Research/deep-research mode can run far more search passes than a single normal response.

---

## 8. The Two-Tier Output System

This is the mechanism that makes the 25-company cap in Section 7 actually work, rather than just being a wall you hit.

**When it kicks in:** only when your candidate pool — every company you named, plus (if discovery is on) every NAICS-discovered candidate — adds up to more than 25. If your total is 25 or fewer, none of this applies; you get a single tracker with full research on everyone, exactly like before.

**Tier 1 selection.** Before doing full research on anyone, Claude runs a fast, cheap qualification pass across the whole pool — does the company plausibly fit your stated NAICS code(s) and industry emphasis, and a rough size/relevance read. This is deliberately *not* the full rating rubric (Opportunity Fit, Growth Signal, etc.) — using the expensive rating system to decide who's worth the expensive research would defeat the point of a cheap filter. Companies you explicitly named get a fixed bonus in this ranking — they aren't automatically guaranteed a slot if your list is very long, but they should usually outrank a comparable NAICS-discovered candidate. The top 25 from this ranking get full research — every column described in Section 11.

**Tier 2 — everyone else.** Added as a second, clearly labeled sheet: "Tier 2 — Additional Candidates (Basic Info Only)." Seven columns, and nothing heavier: Company, Website, Industry / Sector, NAICS Code, NAICS Code Type, Why This NAICS Code, HQ Location / Footprint. No revenue, no hiring signals, no contacts — none of the research that makes Tier 1 slow. There's also a **Promote to Tier 1?** column, left entirely blank for you — see the workflow below.

**How Tier 2 gets sourced cheaply.** Rather than researching each candidate individually, the prompt asks Claude to use searches that surface many companies at once — "top companies in [industry]" roundups, and especially industry market-report vendor lists (e.g. "[industry] market report key players"), which tend to return the most companies per search. Claude keeps trying new query angles until two consecutive searches each add fewer than about 3 new companies, then stops — this is an adaptive stopping rule, not a fixed target count, so it won't burn search budget chasing diminishing returns once a topic is genuinely exhausted. Tier 2 is also capped at roughly 75 rows regardless of remaining budget. Claude reports how many searches it ran and roughly what yield it got, so you can tell genuine saturation apart from just giving up early.

**Include large diversified players in Tier 2?** A toggle in Section 3, off by default. Broad vendor-list searches often surface large, diversified companies where your stated industry is one product line among many, not their core business — think a broad industrial or networking conglomerate that also happens to sell into your space. Left off, Tier 2 stays focused on genuine specialists. Turned on, those diversified players are included, but kept in their own clearly labeled block, visually separate from the focused list — "fits the industry" means something different for a diversified player than it does for a specialist, and the tab doesn't blend the two together.

**Dedup.** Two entries count as the same company if their names match case-insensitively after stripping suffixes like Inc./LLC/Corp./Ltd./Co., or if they share the same website domain. If a company you named also turns up through discovery, it stays a single Tier 1 candidate under your original name — it never becomes a duplicate row.

**Closing the loop back to Tier 1.** Once you have your Tier 2 list, mark **Y** in the Promote to Tier 1? column for whichever companies you want deep-researched next. Copy just those company names, and run this tool again with **Discovery scope** set to **Just enrich these** (see Section 3) — that mode researches only the exact names you give it, at full Tier 1 depth, no new discovery. This is the same "Just enrich these" mode that already existed for other purposes; the Promote column just gives you a clean way to decide what to paste there next.

---

## 9. Typical workflow, start to finish

1. Open `prompt_builder.html`.
2. Fill in whatever starting-point info you have.
3. Set your scope, purpose, and (if relevant) M&A angle.
4. Copy the prompt from the right-hand panel.
5. Paste it into a new Claude chat and send it.
6. Download the `.xlsx` tracker Claude produces.
7. Repeat for other categories/NAICS codes, merging results into one master tracker as you go.

---

## 10. Quick troubleshooting

| Problem | Fix |
|---|---|
| The file opens as code/text instead of a page | Right-click → Open with → your browser |
| "Copy prompt" doesn't seem to do anything | Some browsers silently block clipboard access — use **Download .txt** instead |
| Prompt panel just shows placeholder text | You need at least one starting-point field or a purpose filled in |
| Saved templates disappeared | Templates only last for the current browser tab/session — they aren't saved to disk |
| Output rows feel thin/generic | Check whether your list triggered the two-tier system (Section 8) — if so, thin rows are likely from Tier 2, which is basic-info-only by design, not a research shortfall. If a Tier 1 row (full research) feels thin, that's a genuine gap — try narrowing scope or re-running just that company. |

---

## 11. What's in the Output Tracker

The prompt asks Claude to research and fill in these columns for every company, one row each:

Company, Website, **Careers Page** (a direct link to the company's careers/jobs listing page specifically, not just the homepage — left blank rather than guessed if none is findable), Industry / Sector, **Industry Emphasized** (the specific niche or market segment a company plays in, not just the broad sector), NAICS Code, NAICS Code Type, Why This NAICS Code, HQ Location / Footprint, Company Size, Revenue Band / Latest Revenue, Growth / Revenue Signal, Hiring Signal, **Recent Hiring Trends** (High/Medium/Low pulled from actual current job postings — LinkedIn Jobs, Indeed, the company's careers page — as of the day the report is run), **Salary Range (if posted)** (pulled from the same job-posting check as Recent Hiring Trends — reported with the job title it's attached to when a posting discloses one, left blank rather than estimated when none does), **Opportunity Relevance** (a general-purpose relevance rating that works whether you're job hunting, prospecting, or scouting M&A targets — no longer tied to one specific industry label), Opportunity Fit, Category, Why This Fits, **Executive Role Fit** (the level most worth targeting at this company — Partner, Managing Director, Practice Lead, VP, Chief Consultant, etc. — based on how the company is actually structured), **Warm Introduction Path** (the most plausible route in — recruiter, executive search, former colleagues, a LinkedIn 2nd-degree connection, conference contacts), Outreach Approach, Key Contacts / Priority Titles, Suggested Search Keywords, **Suggested Job Title Keywords** (job posting search terms, distinct from the people-search terms in Suggested Search Keywords), Source URL, Priority Score, Status, Next Action, and Date Researched. That's 31 columns total. If you turned on M&A columns, five more get added on top of that (36 total).

The additions worth knowing about specifically:

- **Careers Page** sits right next to Website. It's specifically the company's own jobs/careers listing page (or its Workday/Greenhouse/Lever posting board) rather than the general homepage — useful as a one-click jump straight to open roles without a search step in between.
- **Industry Emphasized** sits right next to Industry/Sector and adds the market-positioning detail a broad sector label misses — e.g. two companies can both say "Cybersecurity" under Industry/Sector, but one emphasizes OT/industrial security and the other emphasizes cloud-native app security. This column is where that distinction shows up.
- **Salary Range (if posted)** rides along with the Recent Hiring Trends check rather than triggering a separate research pass — if a posting Claude already looked at discloses a range (increasingly common due to state pay-transparency laws), it's reported here with the specific title it came from. Most rows will legitimately be blank, since not every state or company discloses this.
- **Hiring Signal** and **Recent Hiring Trends** sit next to each other but measure two different things. **Hiring Signal** is the indirect read — inferred from overall business trajectory: revenue growth, expansion announcements, funding rounds, earnings commentary. **Recent Hiring Trends** is the direct, concrete read — actual current job postings on LinkedIn Jobs, Indeed, or the company's own careers page, as of the day the report runs. A company can score High on one and Low on the other — e.g. strong revenue growth (High Hiring Signal) but a recent hiring freeze (Low Recent Hiring Trends), or vice versa. Because Recent Hiring Trends is a live snapshot, re-run the prompt later for a fresh read rather than trusting an old tracker's number.
- **Opportunity Relevance** replaced an earlier version of this column that baked a specific industry into its own name (like "OT Cybersecurity Relevance"). It's now generic on purpose, so the same tool works cleanly whether your purpose is a job search, sales prospecting, partnership scouting, or anything else — the relevance judgment still happens, it's just not hard-coded to one field.
- **Executive Role Fit** and **Warm Introduction Path** sit next to Why This Fits and are aimed squarely at outreach planning — the first tells you who to target, the second tells you how you're most likely to actually reach them.
- **Suggested Search Keywords** and **Suggested Job Title Keywords** sit next to each other but search for different things. Suggested Search Keywords is for finding *people* — the right person at a company on LinkedIn. Suggested Job Title Keywords is for finding *postings* — 2–4 actual job title variants that specific company would plausibly use, tailored to its Executive Role Fit rather than a generic title (e.g. "VP, Professional Services" for an OT security vendor vs. "Partner, Cyber Security Services" for a Big 4 firm). If you filled in **Your background**, this column also gets sharpened using that context.
- **Key Contacts / Priority Titles** can carry a second line for publicly traded companies — a named cybersecurity executive sourced directly from the company's 10-K, where disclosed. See Section 17 for what this does and doesn't cover.

## 12. Reading the Formatted Tracker

If you've asked Claude to build the tracker (rather than just generating the prompt), the resulting `.xlsx` comes with formatting built in — not just raw data:

- **Color-coded ratings.** The five rating columns (Growth/Revenue Signal, Hiring Signal, Recent Hiring Trends, Opportunity Relevance, Opportunity Fit) are shaded on a 5-step gradient — green for High, down through yellow-green, yellow, orange, to red for Low (with a slightly darker green for "Very High" where that applies). The color keys off the leading word of the cell, so a cell reading "Medium-High — 149 roles posted..." gets colored for Medium-High. A color legend lives on the **Notes & Assumptions** tab.
- **Suggested Priority Rank (1-25).** A single numeric column sitting right next to the blank Priority Score column. It's a mechanical starting point, not a replacement for your judgment — it weighs Opportunity Fit and Opportunity Relevance heavily (up to 10 points each) and blends the three momentum columns (Growth/Revenue Signal, Hiring Signal, Recent Hiring Trends) as lighter supporting evidence (up to 5 points combined). Hover the column header for a tooltip restating the formula. Use it to get a rough sort order, then compare it against your own Priority Score and overrule it where you disagree — the two columns sit side by side specifically so you can do that comparison at a glance.
- **Website is clickable.** Source URL is left as plain text on purpose — those cells are often citation notes rather than single clean links, so auto-linking them risked producing broken links.
- **Autofilter and frozen panes.** The header row has filter arrows built in, and both the header row and the Company column stay visible while you scroll.
- **Zebra striping** on alternating rows to make it easier to track a row across all the columns.
- **Priority Score, Status, and Next Action** — the three columns meant for you to fill in by hand — get a distinct pale blue fill with a navy left border, so it's visually obvious which columns are Claude's research and which are yours.
- **A Summary tab** with quick counts (companies by Opportunity Fit, by NAICS Code Type, by Category) and a Top 5 by Suggested Priority Rank table, so you don't have to scroll the full sheet to get the gist.

As of this version, all of this is spelled out directly in the generated prompt itself (as long as **Include full visual formatting** is set to Yes, which is the default) — so you get the same formatted output in any chat, not just one that already knows these conventions from earlier context. If you deliberately turned that toggle to **No**, you'll get a plain data-only spreadsheet instead — no colors, no Suggested Priority Rank, no extra tabs.

## 13. The Job Posting Quick Links Tab (and Its Limits)

If **Add a Job Posting Quick Links tab?** is Yes, the tracker gets a second sheet — one row per company, with three `HYPERLINK()` formulas: a LinkedIn Jobs search, an Indeed search, and a Google Jobs search, each pre-filled with that company's name and one specific job title (pulled from Suggested Job Title Keywords — just the single most likely title, not the whole multi-title cell, so the search stays focused).

**Say this plainly, because it's easy to misread at a glance: this tab does not contain jobs. It contains links.** Clicking a link just opens LinkedIn, Indeed, or Google with the company name and a job title already typed into the search box for you — exactly as if you'd typed them in yourself. It is not pulling in, listing, or storing any actual postings, and nothing on this tab is "jobs found" or "results" — it's a shortcut to go *run* that search, fresh, live, every single time you click it. Open the file a year from now and the links still work; they'll just show you whatever happens to be posted *at that moment*, not anything from when the file was built.

A few other things worth knowing:

- **The links are real formulas, not static text.** They reference that row's Company and Job Title cells on the same tab, so if you edit either one later, the link updates automatically — nothing needs to be regenerated by hand.
- **The exact formula pattern matters.** These use Excel's `ENCODEURL()` function to handle spaces and special characters in company names and job titles correctly. When Claude writes this formula for you, it needs the `_xlfn.` prefix (e.g. `_xlfn.ENCODEURL(A2)`) — Excel requires that prefix for functions added after the original file-format spec, and leaving it off produces a `#NAME?` error instead of a working link. This has been tested and confirmed working with the prefix.
- **Known issue, now fixed:** earlier versions of the generated prompt occasionally came back with cells showing literal broken text like `[hashtag#Name](linkedin.com/feed/hashtag/...)` instead of working links. That was Claude substituting LinkedIn's hashtag/feed URL for the actual jobs-search URL, and writing it as Markdown link syntax instead of a real `=HYPERLINK()` formula (Excel doesn't render Markdown, so it just shows as text). The prompt now explicitly calls out both mistakes and asks Claude to verify a sample of links before finishing. If you regenerate a prompt from an older saved copy of this tool, re-copy it from the current version to pick up that fix.
- **This is deliberately the cheap, safe option.** Building it costs no extra research — it's pure string templating from data Claude already generated in the main tracker. That's why it defaults to Yes.

**If you actually want real postings** — a table of specific job titles, companies, and URLs, not just search links — that's a different, deliberately separate tool from either tab on this page. Live postings data has a much shorter shelf life than company research (postings turn over weekly; company revenue/HQ/size is stable for months), and getting real results means live web search per company on top of the research already happening — so bundling it into this same prompt would either bloat the request or go stale inside the same file as more durable data. Ask about a companion live-postings-research prompt if you want that — it's built to take a shortlist of companies (ideally your top few by Suggested Priority Rank, not all of them) and their Suggested Job Title Keywords as input, and return actual postings. Don't confuse it with the Job Post Finder tab in Section 13 below — that one is a static copy of data already in this tracker, not a live search.

## 14. The Job Post Finder Tab

If **Add a Job Post Finder tab?** is Yes, the tracker gets a third, deliberately minimal sheet: **Company Name** in column A, **Suggested Job Title Keywords** in column B, one row per company, in the same order as the main tracker. Nothing else — no formulas, no hyperlinks, no job-board-specific columns.

This is a different tool for a different moment than the Job Posting Quick Links tab covered in Section 13:

- **Job Posting Quick Links** gives you pre-built, clickable search links — but only to three specific platforms (LinkedIn, Indeed, Google Jobs), and only using a single job title per company (the first variant pulled from Suggested Job Title Keywords, to keep each search focused).
- **Job Post Finder** gives you the raw ingredients instead — the full Suggested Job Title Keywords cell, all 2-4 title variants included, sitting right next to the company name so you can select both, copy, and paste into whatever job board, search engine, or internal tool you actually want to use — not just the three the Quick Links tab is hardcoded to.

The intended workflow: run your target list first, then come to this tab as a simple reference sheet — highlight a row, copy the company name and its keyword variants, and paste them wherever you're searching that day. Because it's plain data with no live links to maintain, it also survives being copied out to somewhere else (a notes app, a second spreadsheet, a task tracker) without losing anything, unlike the HYPERLINK() formulas on the Quick Links tab, which only work inside the original file.

Like the Quick Links tab, this one costs no extra research to build — it's pure copy-through of data Claude already generated for the main tracker — which is why it also defaults to Yes.

## 15. The Industry Events & Forums Tab (and How Category Drives It)

If **Add an Industry Events & Forums tab?** is Yes, the tracker gets a tab listing real, upcoming conferences and trade shows relevant to your stated industry/purpose — Event Name, Date(s), Location, Format (in-person/virtual/hybrid), Relevant To, and URL.

The one field worth understanding is **Relevant To**. Events aren't company-specific the way the rest of this tracker is — the same conference is often relevant to several companies on your list at once, so this tab is one row per *event*, not one row per company. To keep it connected back to your company list without hard-linking to individual rows (which would break the moment you added or removed a company), **Relevant To reuses the exact values from your main sheet's Category column** rather than inventing a separate industry taxonomy. Whatever grouping logic Claude used to sort your companies — by sub-industry, by NAICS code type, by company role, whatever made sense for your purpose — is the same grouping this tab uses to connect events back to them.

Practically, that means if your Category column has values like "OT Cybersecurity Vendor — Practice/Professional Services Leadership" and "Big 4 / Tier 1 Consulting," this tab's Relevant To column will use those same phrases, not a generic "Cybersecurity" or "Consulting" label — so you can quickly see which events matter for which cluster of companies you're already tracking.

Same honesty standard as everywhere else in this tracker: only real, currently findable events with a real URL are included. If coverage for a given Category is thin, that's reported directly rather than an event getting invented to fill the gap.

## 16. The Company Activity & Events Tab

If **Add a Company Activity & Events tab?** is set to Yes (it's **off by default**), the tracker gets a tab that flips the Industry Events tab's structure around: one row per *company* instead of per event, tracking that specific company's own public footprint — recent LinkedIn activity, podcast/webcast appearances, and upcoming events it's attending, sponsoring, or speaking at.

This is a meaningfully harder research task than the Industry Events tab, which is why it's opt-in rather than on by default:

- **Industry Events** searches for a bounded, discoverable set of things — real conferences in a real industry, which tend to have their own marketing and show up reliably in search.
- **Company Activity** asks "what has this *specific* company been doing publicly, lately" — a much narrower, noisier search per company, and many companies (especially smaller/private ones) simply don't have much of a public footprint to find.

To get better coverage, the prompt tells Claude to check each company from a few different angles — the company's own LinkedIn page directly, a podcast/webcast search, and a conference/sponsor search — rather than giving up after one generic search. Even so, **expect real unevenness**: some companies will have a rich trail of recent activity, and many rows will legitimately read "No recent public activity found." That's the honest result, not a sign something's broken — Claude is explicitly told not to invent a LinkedIn post, podcast appearance, or event that doesn't actually exist just to fill a cell. If most of your list comes back empty, check the Notes tab first — it should say what was actually searched, so you can tell "nothing found" apart from "not really checked."

## 17. Key Contacts and 10-K Filings

The Key Contacts / Priority Titles column normally identifies the practice-level person worth targeting at a company — a Managing Director, VP, or Practice Lead, based on how that company is structured. As of this version, there's a second, narrower data point layered on top of that for **publicly traded companies specifically**: a check of the company's most recent 10-K for a named individual responsible for cybersecurity governance.

Since 2023, SEC rules (Regulation S-K Item 106 / Item 1C of the 10-K) have required public companies to describe who's responsible for managing cybersecurity risk, and a majority of large public filers do name that person — usually a CISO, sometimes a CIO or CTO. When Claude finds one, it's added as a clearly labeled second line — "(per FY20XX 10-K)" — kept visually separate from the practice-level contact above it, since one is inferred from research and the other is sourced directly from a regulatory filing.

Worth knowing the real limits here before treating this as a bigger feature than it is:

- **Only applies to companies that file a 10-K at all.** Most pure-play OT vendors on a typical list (Dragos, Claroty, Nozomi, Armis) are privately held — no 10-K exists, so nothing gets added for them, and the column doesn't clutter itself with a "not applicable" line for the obvious case.
- **It's the enterprise-wide security executive, not an OT-specific one.** A named CISO at a Big 4 firm or a public vendor tells you who owns cybersecurity risk company-wide — it's a useful *additional* data point, not a replacement for the practice-level targeting the rest of the column already does.
- **Not every public company names someone.** Many disclosures describe the responsible role without naming the individual. When that happens, the tracker says so directly rather than silently leaving the company looking unchecked.
- **It's only as current as the filing.** A 10-K is annual — the named person could have moved on since the most recent filing.

## 18. Compensation Benchmark

Right next to the 10-K contact check sits a related, narrower data point: if the named individual from that 10-K also shows up in the company's proxy statement (DEF 14A) as a Named Executive Officer, their disclosed total compensation gets reported alongside them — e.g. "$2.1M total comp, FY2025 proxy."

Set expectations accordingly: **this will genuinely apply to a minority of the companies on your list.** Proxy statements only disclose compensation for a handful of the most highly paid executives at a company (typically the top 5) — a security-specific role like CISO is rarely in that group unless it happens to also be, say, the CTO or another top-5 role. When it doesn't apply, the tracker says so directly ("not a Named Executive Officer — not disclosed") rather than leaving the cell ambiguously blank or substituting a generic market-rate guess dressed up as filing data.

Think of this one as a bonus when it fires, not something to plan around — it's a nice, free negotiation data point for the handful of companies where it happens to apply, layered on top of a feature (the 10-K contact check) that itself only applies to public companies in the first place.

## 19. Step 2 — LinkedIn Contact Enrichment

Below the main prompt panel is a second, self-contained card: **Step 2 (optional) — LinkedIn Contact Enrichment**. This is a separate feature from everything above it — it doesn't touch or require the main tracker at all, and it generates its own standalone prompt with its own Copy/Download buttons.

**What it does:** cross-references a LinkedIn contacts export against a list of target companies, to surface which of your existing connections work (or worked) at each one — a starting point for warm introductions.

**How to use it:**

1. Paste your target companies into the box, one per line. The easiest source is the Company column from a tracker this tool already helped you build — copy that column and paste it in directly.
2. Keep the list to **25 companies or fewer**. The tool will warn you inline if you go over. This isn't an arbitrary cap: the contact-matching work scales with how many companies Claude has to fuzzy-match every single contact in your export against, so a long list here makes the task slower and can hurt match accuracy — unlike the main tracker, where the expensive part is researching each company, here the expensive part is the number of *contacts*, which doesn't shrink no matter how you trim the company list. Fewer companies just keeps the matching focused and the output easy to review.
3. Copy or download the generated prompt.
4. Start a **new** Claude conversation, paste the prompt in, and **attach your LinkedIn contacts CSV export directly to that same message**. This tool never uploads, parses, or even reads the CSV itself — same "nothing you enter is sent anywhere" design as the rest of the page. Claude reads the attached file natively once you send it.

**What you get back:** for each target company, any matching contacts found in your export — name, title, LinkedIn profile URL (if present), whether they currently or formerly worked there, and a Match Confidence rating (High/Medium/Low) reflecting how exact the company-name match was. Companies with no match are still listed as "No match found" rather than dropped, so you can see coverage across your whole list at a glance. Same honesty standard as the rest of this tool: Claude is told not to fabricate a contact or guess someone into a company they aren't actually listed against in your file.

This is a genuinely separate run from your main tracker — think of it as a follow-up step once you already have a shortlist, not something to run alongside the initial research.

## 20. A Faster Way to Fill This Out (reverse note)

If you'd rather not use the web form at all, there's a companion plain-text template — `Target_Company_Research_Prompt_Template` (.md) — with the same fields laid out as fill-in-the-blank text you can paste directly into a Claude chat. Use whichever format is more convenient in the moment; both produce the same result.
