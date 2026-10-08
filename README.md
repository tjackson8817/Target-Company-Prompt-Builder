# Target Company Research Prompt Builder

A free, browser-based tool that turns a form into ready-to-paste prompts for Claude — the prompts ask Claude to research target companies and build a fully formatted Excel tracker, for job search, sales prospecting, partnerships, or M&A research.

**No installation needed.** Open `prompt_builder.html` in any modern browser. Fill in what you know, copy or download the generated prompt(s), and paste into a Claude conversation (with web search and code execution enabled) to generate the actual workbook. Nothing you enter is sent anywhere — this page only builds text locally in your browser.

## How it works

The page is organized into **Shared Inputs** plus three linked, independently-runnable prompt sections:

1. **Shared Inputs** — company names you already know, an industry description, and/or NAICS codes; optional exclude list, company-size filter, and location-radius filter. Fill this in once; all three sections below read from it.
2. **Section 1 — Detailed Company Pull** — the main tool. Choose Discovery scope: "Find new companies" (Claude does its own modest discovery, bundled into full research) or "Just enrich these" (research only the exact companies you typed — the right choice if you pasted a pruned Section 2 list into Shared Inputs). Describe what the list is for — this is the single most important field, since it drives how Claude judges fit, category, and contacts for every company. Toggle optional add-ons and, if using "Find new companies," an optional manual two-tier output.
3. **Section 2 — Bulk Company Pull** *(optional)* — a fast, wide, low-detail prompt: turns your Shared Inputs into a large flat list of candidate companies (Company, Website, Inferred NAICS Code, one-line description, Source) for you to prune by hand. No per-company research cost, so it can go wider than Section 1's practical ceiling. Use it when you want a large candidate pool to review and prune, then feed the survivors back into Section 1 with "Just enrich these."
4. **Section 3 — LinkedIn Contact Enrichment** *(optional, standalone)* — maps a shortlist of target companies (25 or fewer) to your LinkedIn connections to surface warm introduction paths. Attach just your `Connections.csv` for a company-to-connection map, or attach `messages.csv` too and the workbook also shows your message history with each matched connection: who you've talked to, who's waiting on your reply, and who you've never contacted. Doesn't touch or require the Section 1 tracker.

Each section has its own Copy prompt / Download .txt buttons and its own live-updating output panel — they're three separate prompts meant to run as separate Claude conversations or messages, not one combined prompt.

## How companies actually get discovered

Not a NAICS-code search. A NAICS code alone is far too broad to filter by — it would return any IT/consulting business in North America — and the one government source that can filter registered companies by NAICS code, SAM.gov's entity search, blocks automated access. Discovery (in both Section 1's "Find new companies" mode and Section 2) instead runs:

1. **Competitor/alternative cascade** — searches "[company] competitors" and "[company] alternatives" for each company you named, repeating outward for companies found that way too.
2. **Analyst & category sources** — Gartner Magic Quadrant / Forrester Wave entries, G2/Capterra category pages, or equivalent category-leader lists.
3. **Conference exhibitor/sponsor lists** — a strong signal for "real company actively in this space."
4. **Live job-posting search** — surfaces companies actively hiring in the space, doubling as a real hiring-signal data point.

NAICS codes are applied to each company *after* it's found this way — a classification tag (up to 5 per company: 1 primary + up to 4 secondary), stated alongside the keyword used to derive them so you can catch a bad extraction — not the discovery engine itself.

## Key features

- **Bulk Company Pull (Section 2)** — cheap, wide-net discovery for pruning by hand before committing to full research; feeds back into Section 1 via its Company column
- **Manual, adjustable two-tier output (Section 1, optional)** — turn on "Use a two-tier target list?" and set your own Tier 1 / Tier 2 sizes to get a fully-researched Tier 1 plus a lighter Tier 2 for a larger discovered pool. Only takes effect when Discovery scope is "Find new companies" — it's inert in "Just enrich these" mode, since there's no discovered pool to rank
- **Company size filter** *(optional)* — e.g. "under 1,000 employees"; leave blank to include all sizes
- **Location radius filter** *(optional)* — a ZIP code and a radius in miles (default 100); leave the ZIP blank for no distance restriction. Separate from "Preferred location / work arrangement," which is about your own job-search preferences, not a company-distance filter
- **M&A research columns** *(optional)* — ownership type, recent M&A activity, deal-size fit, and acquisition/acquirer role fit
- **Job Posting Quick Links tab** *(optional, on by default)* — one row per company with live HYPERLINK() search links to LinkedIn Jobs, Indeed, and Google Jobs
- **Job Post Finder tab** *(optional, on by default)* — a simpler tab: Company Name and the full Suggested Job Title Keywords cell, no formulas or links, for pasting into whatever job board you actually want to use
- **Outreach Contacts tab** *(optional, on by default)* — Company, Key Contacts / Priority Titles, Warm Introduction Path, and Category side by side, formatted for pasting into the companion Outreach Message Builder tool
- **Industry Events & Forums tab** *(optional, on by default)* — real, currently findable conferences and trade shows relevant to your industry, one row per event
- **Company Activity & Events tab** *(optional, off by default)* — one row per *company*: recent LinkedIn activity, podcast/webcast appearances, upcoming events. A harder, less reliable research task than Industry Events, so it's opt-in and carries an explicit "leave it blank rather than fabricate" instruction
- **LinkedIn Contact Enrichment workbook (Section 3)** — a 4-tab .xlsx: **Summary** (per-company coverage and outreach counts, all live formulas), **Contact Matches** (target companies mapped to connections, with Current/Former, Match Confidence, and a Match Note for any non-exact match), **Target Connections** (each matched connection's message history rolled up into a status: Never messaged / You reached out / They reached out / Awaiting their reply / Your move), and **Messages** (the full conversation history). The last two tabs need `messages.csv`; with `Connections.csv` alone you still get Summary and Contact Matches
- **Templates** — save your current field values (including Section 1's tier sizes and Section 2's target list size) under a name and reload later; session-only, not saved across a page reload
- **31 research columns per company** in the Section 1 tracker (36 with M&A columns on), including a direct careers-page link alongside the website, up to 5 NAICS codes per company with keyword-extraction transparency, a salary range column pulled from current job postings where disclosed, growth/hiring signals, opportunity fit, warm introduction paths, and (for public companies) named CISO/CIO/CTO disclosures pulled from 10-K cybersecurity governance sections and executive compensation from proxy statements where applicable

## Files in this repo

| File | Purpose |
|------|---------|
| `prompt_builder.html` | The tool itself — open it in a browser |
| `Prompt_Builder_User_Guide.md` / `.docx` | Full user guide, same content in both formats |
| `Target_Company_Research_Prompt_Template.md` | Fill-in-the-blank plain-text alternative to the web form for Section 1 — paste directly into Claude |
| `sample_bulk_company_pull_prompt.txt` / `sample_bulk_company_pull_output.xlsx` | Real example of Section 2 — 25 named companies in, 74-company flat candidate list out |
| `sample_find_new_companies_prompt.txt` / `sample_find_new_companies_output.xlsx` | Real example of Section 1 in "Find new companies" mode with two-tier output on |
| `sample_just_enrich_these_prompt.txt` / `sample_just_enrich_these_output.xlsx` | Real example of Section 1 in "Just enrich these" mode — 25 named companies, full 9-tab tracker |
| `sample_linkedin_contact_enrichment_prompt.txt` / `sample_linkedin_contact_enrichment_output.xlsx` | Example of Section 3 with Connections + Messages — 15 target companies, 4-tab workbook. Built from **fictional** contacts and messages so no one's real network or private conversations are published |

## Important notes

- **Section 3 and your privacy:** `messages.csv` contains your private LinkedIn conversations, and the workbook's Messages tab copies them. Treat the output as personal — don't commit it to a public repo or share it as-is. Choose "Connections only" if you'd rather not share your message history with Claude at all.

- This tool **generates prompts** — it does not itself call any AI model or produce the Excel file. You paste the output into a separate Claude conversation to get the actual workbook.
- For best results, use a Claude conversation with **web search** and **code execution and file creation** both enabled, since the generated prompts ask Claude to research real, current information and build a real .xlsx.
- Company size and location filters are instructions to Claude, not a guaranteed hard filter against a live database — spot-check a sample of results.
- There's no automatic company cap. As a practical guide, totals above roughly 50–75 companies in one Section 1 run tend to come back thinner per company — use Section 2 (Bulk Company Pull) plus "Just enrich these" for anything larger, or set an explicit two-tier split.
