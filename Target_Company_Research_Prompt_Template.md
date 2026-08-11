# Target Company Research → Excel Tracker
### Reusable Prompt Template (with NAICS Discovery)

Copy everything below into a new Claude chat. Fill in the fields at the top — you don't need to know anything about NAICS codes to use this — delete anything you don't need, and send it. Claude will figure out the codes, find candidate companies, research them, and build a formatted, ready-to-edit .xlsx tracker. Works for any purpose — job search, sales prospecting, partnership scouting, investment research, vendor evaluation, etc.

---

## FILL THIS IN

**Starting point** *(fill in whichever of these you actually have — one is enough, use as many as apply)*

- **Company(s) you know** (current employer, former employer, a competitor, anyone): `[Company name(s), or leave blank]`
- **Industry / field, in plain language** (no jargon needed): `[e.g. "industrial cybersecurity consulting" / "commercial HVAC controls" / "specialty coffee roasting" — or leave blank. This word/phrase is reused below as a column label, so be specific.]`
- **NAICS code(s), if you already happen to know them:** `[leave blank if unknown or not applicable]`

**Exclude these companies** *(optional — leave out entirely even if they'd otherwise match)*
`[Company name(s), or leave blank]`

**Limit to company size — optional** *(e.g. "under 1,000 employees" — leave blank to include all sizes)*
`[Size filter, or leave blank]`

**Limit to a location radius — optional** *(enter a ZIP code and a radius to restrict results to companies headquartered within that distance; leave the ZIP blank for no distance restriction — separate from "Preferred location / work arrangement" below, which is about your own preferences, not a company-distance filter)*
`[ZIP code, or leave blank]`
`[Radius in miles — default 100 if a ZIP is given]`

**Discovery Scope** *(this controls what Claude actually does with the above)*
`[Find new companies via NAICS discovery / Just enrich the companies I listed — default: Find new companies]`

**How many companies per code, roughly?**
`[e.g. 15–30 — or leave blank for Claude's judgment]`

**Include secondary / adjacent NAICS codes?** *(suppliers, vendors, and related-but-differently-classified industries — recommended if you want to broaden beyond your exact niche)*
`[Yes / No — default Yes if left blank]`

**What is this list for?** *(tells Claude how to fill in "Category," "Key Contact," "Opportunity Fit," and "Why This Fits")*
`[e.g. "job search targets for a VP of Sales role" / "prospective customers for our SaaS product" / "potential acquisition targets" / "partnership candidates"]`

**Preferred location / work arrangement — optional:**
`[e.g. "Texas or remote" / "must have EU presence" / leave blank if no preference]`

**Your background — optional** *(paste resume, CV, bio, LinkedIn summary, or a few lines of relevant experience — no length limit, but a tight paragraph of highlights tends to work better than a full multi-page document; sharpens Suggested Job Title Keywords and Warm Introduction Path)*
`[e.g. "8 years in federal OT cybersecurity consulting, former Booz Allen and SAIC" — or leave blank]`

**Include full visual formatting in the tracker?** *(color-coded rating columns, computed Suggested Priority Rank, clickable Website links, autofilter, frozen panes, zebra striping, Notes/Summary tabs)*
`[Yes / No — default Yes if left blank. "No" gets you a plain data-only spreadsheet instead.]`

**Add a Job Posting Quick Links tab?** *(one-click LinkedIn Jobs, Indeed, and Google Jobs search links per company, built from Company + Suggested Job Title Keywords — a search-link generator, not real postings data)*
`[Yes / No — default Yes if left blank]`

**Add an Industry Events & Forums tab?** *(real, upcoming conferences and trade shows relevant to your industry/purpose — one row per event, not per company; the Relevant To field reuses your Category column)*
`[Yes / No — default Yes if left blank]`
`How far ahead: [Next 6 months / Next 12 months / Any upcoming — default 12 months]`

**Add a Company Activity & Events tab? — optional** *(different from the tab above: one row per COMPANY, not per event — recent LinkedIn activity, podcast/webcast appearances, and upcoming events/tradeshows that specific company is attending or speaking at. Harder to verify reliably than a public conference calendar, so it defaults off. Same honesty standard applies — expect "No recent public activity found" for many companies rather than invented activity.)*
`[Yes / No — default No if left blank]`
`How far back for recent activity: [Last 30 days / Last 90 days / Last 6 months — default 90 days]`

**M&A research columns — optional** *(leave this whole section out if not relevant)*
- Add M&A-specific columns? `[Yes / No]`
- If yes, angle: `[Find acquisition targets / Find likely acquirers / Show fit for either]`

---

## PROMPT (send as-is after filling in the section above)

Please execute this task directly — research and build the actual file now, rather than first describing your plan, summarizing what you're about to do, or offering recommendations about how to proceed. If a genuine capability limitation prevents you from completing part of this (e.g., no file-creation tool available, no web search), say so plainly and do as much as you actually can — but don't pause to ask permission, outline an approach, or check in before starting the real work.

I want you to research target companies and build a formatted Excel tracker (.xlsx). Here's what I have:

- Company/companies I know: *(from above)*
- Industry / field (plain language): *(from above)*
- NAICS code(s) I already know: *(from above)*
- Discovery scope: *(from above)*
- Roughly how many companies per NAICS code: *(from above)*
- Include secondary/adjacent NAICS codes: *(from above)*
- Exclude these companies entirely, even if they'd otherwise match: *(from above, if any)*
- Company size filter, if given above: only include companies matching that size band — exclude companies outside it.
- Location filter, if a ZIP was given above: only include companies headquartered within the given radius of that ZIP code. Estimate the distance from each company's HQ to the ZIP code and note the approximate mileage as part of the HQ Location / Footprint column.
- What this list is for: *(from above)*
- Preferred location / work arrangement: *(from above, if any)*
- My background, if I shared it above: use it to sharpen Suggested Job Title Keywords and Warm Introduction Path — look for former-employer overlap, transferable experience, or relevant credentials.
- M&A research angle, if requested above: treat each company accordingly and add the M&A columns described below.

### Step 1 — Confirm the industry/focus context
Use the industry/field description I gave (or infer one from the companies I named) as context for judging the Opportunity Relevance column below — this column stays generically named regardless of my industry, since the same tracker structure should work for any purpose.

### Step 2 — Look up NAICS code(s)
If I didn't give a NAICS code, determine the most appropriate primary code(s) from my industry description or named companies. If "include secondary/adjacent codes" is Yes, also identify relevant secondary/adjacent codes (suppliers, related disciplines).

### Step 3 — Build the candidate company list
For each NAICS code (primary and secondary), generate real, currently-operating companies under that code — a mix of well-known and lesser-known names where possible, prioritizing my stated company-size and location preferences if I gave any. Use the "how many per code" number I gave above as a target (roughly, not a hard cap). Exclude any company I listed in "Exclude these companies." If discovery scope is "Just enrich," skip this step and only use the companies I named directly.

### Step 4 — Research each company and build the Excel tracker
For every company gathered in Step 3 (plus any I named directly), research and build a formatted Excel tracker (.xlsx), one row per company, with these columns:

1. **Company** — legal/common name
2. **Website**
3. **Careers Page** — a direct link to this company's careers/jobs listing page specifically (e.g. "acme.com/careers" or their Workday/Greenhouse/Lever posting board), not just the homepage. Leave blank if you can't find one rather than guessing at a URL pattern
4. **Industry / Sector**
5. **Industry Emphasized** — the specific niche, vertical, or market segment this company emphasizes within that broader sector (e.g. "cloud security for financial services" rather than just "cybersecurity") — gives more market-positioning detail than the sector alone
6. **NAICS Code** — the specific code this company was found under
7. **NAICS Code Type** — Primary or Secondary
8. **Why This NAICS Code** — one line connecting this code back to my starting point (e.g. "Same code as [company I named]" / "Supplier to [industry]" / "Adjacent discipline, different classification")
9. **HQ Location / Footprint** (city, state/country, and whether local, regional, or global)
10. **Company Size** — employee count band
11. **Revenue Band / Latest Revenue** — most recent public figure or reasonable estimate, with source/year noted
12. **Growth / Revenue Signal** — High/Medium/Low plus a brief note on what's driving it
13. **Hiring Signal** — High/Medium/Low plus a brief note, inferred from overall business trajectory (revenue growth, expansion announcements, funding rounds, earnings commentary) and how that connects to my stated purpose — an indirect signal, not a job-posting count
14. **Recent Hiring Trends** — High/Medium/Low based on actual current job postings for this company (check LinkedIn Jobs, Indeed, or the company's own careers page) as of the date this report is run — High = many open roles posted right now, Medium = some open roles, Low = few or no open roles found. This is a direct, concrete snapshot, separate from the broader Hiring Signal above
15. **Salary Range (if posted)** — while checking job postings for the Recent Hiring Trends column above, note the salary range if any posting discloses one (many now do, due to state pay-transparency laws), along with the job title it's attached to (e.g. "$140K-$170K — Sr. OT Security Engineer posting"). Leave blank if no posting discloses a range — don't estimate or infer a figure
16. **Opportunity Relevance** — rate High/Medium/Low with a short note on how relevant this company is to my stated purpose, whatever that purpose is (job search, sales, partnerships, M&A, etc.)
17. **Opportunity Fit** — High/Medium/Low, how well this company fits my stated purpose overall
18. **Category** — group companies usefully for my stated purpose (e.g. by NAICS code type, sub-industry, or company role — infer what's most useful)
19. **Why This Fits** — 1–2 sentence rationale connecting the company to my stated purpose
20. **Executive Role Fit** — the level/title most relevant to approach or target at this company for my purpose (e.g. Partner, Managing Director, Practice Lead, VP, Chief Consultant), based on how the company is structured
21. **Warm Introduction Path** — the most plausible path to a warm introduction at this company (e.g. recruiter, executive search firm, former colleagues, LinkedIn 2nd-degree connection, conference/industry contacts), inferred from the company's profile and my background if I've shared it
22. **Outreach Approach** — brief guidance on how and through whom to approach this company
23. **Key Contacts / Priority Titles** — the person/role most relevant to my purpose, named individuals if publicly findable, otherwise closest equivalent titles. Additionally, for publicly traded companies only, check the most recent 10-K's cybersecurity governance disclosure (Item 1C / Regulation S-K Item 106) for a named CISO, CIO, CTO, or similarly responsible officer. If found, add as a clearly labeled second line: "(per FY20XX 10-K)" — kept visually distinct from the practice-level contact above since it's sourced from a filing, not inferred. If the company is public but no one is named, say so briefly rather than omitting silently. If the company is privately held with no 10-K, skip this entirely.
24. **Compensation Benchmark** — for publicly traded companies only: if the individual named from the 10-K in column 23 also appears in that company's most recent proxy statement (DEF 14A) Summary Compensation Table as a Named Executive Officer, report their total compensation figure with the fiscal year noted (e.g. "$2.1M total comp, FY2025 proxy"). This will genuinely apply to a minority of companies — security-specific roles like CISO are rarely among the top 5 highest-paid executives a proxy discloses. When it doesn't apply, say so briefly ("not a Named Executive Officer — not disclosed") rather than leaving the cell ambiguously blank. Skip entirely for private companies, same as column 23.
25. **Suggested Search Keywords** — terms useful for a LinkedIn people-search (finding the right person at this company)
26. **Suggested Job Title Keywords** — 2–4 actual job title variants this specific company would plausibly use in a job posting for the Executive Role Fit identified above (not a generic title — the title format this company itself tends to use), meant for searching job postings/boards rather than searching for people
27. **Source URL** — link(s) supporting the data above
28. **Priority Score** — leave blank for me to fill in
29. **Status** — leave blank (I will fill in: Not Started / Researching / Contacted / In Progress / Closed)
30. **Next Action** — leave blank
31. **Date Researched** — today's date

*(If M&A columns were requested, also add:)*

32. **Ownership Type** — founder-owned, PE-backed, public, subsidiary
33. **Recent M&A Activity**
34. **Signals** — sale/succession signals (if I'm looking for acquisition targets) or acquisition-appetite signals (if I'm looking for acquirers)
35. **Estimated Deal Size Fit**
36. **M&A Role Fit** — Likely Acquisition Target / Likely Acquirer / Could Be Either / Unclear

### Step 4a — Two-tier output (only relevant if your combined candidate pool is large)

Assemble your full candidate pool first: every company I named above, plus (if discovery scope is "Find new companies") every NAICS-discovered candidate. Do not start full research yet.

- **If that combined pool is 25 companies or fewer:** skip everything below in this step. Research all of them at full depth (all columns above) and output a single tracker, exactly as this template would have worked without this step.
- **If the pool is more than 25:** use the two-tier process below.

**Tier 1 selection** (only when the pool exceeds 25): before doing full research on anyone, run a fast, cheap qualification pass across the whole pool — does the company plausibly fit the stated NAICS code(s) and industry emphasis, and a rough size/relevance read. Do NOT use the full rating rubric (Opportunity Fit, Growth Signal, etc.) for this pass — that comes later and would defeat the point of a cheap filter. Rank the pool using that quick read, and give every company I explicitly named above a fixed bonus in that ranking (they aren't automatically guaranteed a spot if the pool is very large, but they should usually outrank a comparable NAICS-discovered candidate). Select the top 25 and give ONLY those companies the full research described in Step 4 above.

**Tier 2** (everyone else, when the pool exceeds 25): add a second sheet/section, clearly labeled "Tier 2 — Additional Candidates (Basic Info Only)", with exactly these columns and nothing else — no revenue, no hiring signals, no contacts, none of the heavier research above:
- Company
- Website
- Industry / Sector
- NAICS Code
- NAICS Code Type — Primary or Secondary
- Why This NAICS Code
- HQ Location / Footprint
- Promote to Tier 1? — leave entirely blank for me to fill in later; this is not something you research or guess at

Source Tier 2 efficiently: use searches that surface many companies at once — "top companies in [industry/NAICS]" roundups, and especially industry market-report vendor lists (e.g. "[industry] market report key players") — rather than one dedicated search per company. Keep searching with new query angles (different phrasing, sub-segments, regions) until two consecutive searches each add fewer than about 3 new companies not already found, then stop — don't force a fixed target count once yield has genuinely dropped off, and don't let Tier 2 grow past roughly 75 rows regardless of how much search budget remains. Report honestly how many searches you ran and roughly what yield you got, so I know whether you stopped from genuine saturation or just gave up early.

Tier 2 still needs to genuinely fit my stated industry/NAICS/purpose — don't let a broad market-report search turn this into a dump of loosely-related companies just because a source happened to mention them.

Whether to include large, diversified companies where this industry is one product line among many, not their core business (e.g. a broad industrial or networking conglomerate that also sells into this space): *(from above)* — if yes, keep them in their own clearly labeled block within Tier 2, visually separate from the focused/specialist companies above them, since "fits the industry" means something different for a diversified player than a specialist.

Dedup across both tiers: treat two entries as the same company if their names match case-insensitively after stripping suffixes like Inc./LLC/Corp./Ltd./Co., or if they share the same website domain. If a company I explicitly named also turns up via discovery, it's a Tier 1 candidate under my original name — never create a second, separate row for the same company.

Close with a plain-language note (in the Notes tab if formatting is on, otherwise in your reply) telling me: how many total unique candidates you found, how many made Tier 1 vs Tier 2, and reminding me that to research more from Tier 2, I should mark "Y" in the Promote to Tier 1? column for whichever ones I want, then paste just those company names back into the "Company(s) you know" field above with Discovery Scope set to "Just enrich" for a follow-up run.

### Step 5 — Formatting (skip this step entirely if I said "No" to visual formatting above)

Apply all of the following to the Excel file:
- Color-code these five rating columns using a 5-step gradient keyed to the leading word of each cell: Growth / Revenue Signal, Hiring Signal, Recent Hiring Trends, Opportunity Relevance, Opportunity Fit. Very High = darker green (A9D8A9), High = green (C6E8C6), Medium-High = yellow-green (E2EFC0), Medium = yellow (FFF2B2), Low-Medium = orange (FBDCB8), Low = red (F4C7C3).
- Add a "Suggested Priority Rank (1-25)" column positioned immediately next to the blank Priority Score column. Compute it per company: convert each rating word to points (Very High=5, High=4, Medium-High=3.5, Medium=3, Low-Medium=2, Low=1), then score = (Opportunity Fit points x 2) + (Opportunity Relevance points x 2) + average(Growth/Revenue Signal points, Hiring Signal points, Recent Hiring Trends points). Round to 1 decimal. Color this column using the same gradient, bucketed by score: ≥22 Very High, ≥18 High, ≥14 Medium-High, ≥10 Medium, ≥7 Low-Medium, else Low. Add a cell comment on this column's header noting it's a mechanical starting point, not a replacement for my own judgment, and that I should compare it against my own Priority Score.
- Hyperlink the Website and Careers Page columns so each cell links to that company's actual site/careers page. Leave Source URL as plain text (those cells are often citation notes, not single clean links).
- Add autofilter on the header row. Freeze both the header row and the Company column so they stay visible while scrolling.
- Lightly shade alternating data rows (zebra striping) for readability, without overriding the rating-column colors above.
- Give the Priority Score, Status, and Next Action columns (the ones I fill in by hand) a distinct light fill and border, separate from the rating gradient.
- If a Tier 2 sheet exists: give its "Promote to Tier 1?" column that same distinct light fill and border treatment. Add autofilter and freeze the header row on the Tier 2 sheet too. If the adjacent/diversified block exists within it, separate it from the focused list above with a clearly labeled divider row.
- Add a "Notes & Assumptions" tab: document which figures are verified vs. estimated, list key assumptions, and include a color legend explaining the gradient above. If a Tier 2 sheet exists, this is also where the two-tier summary note (search count, yield, Tier 1 vs Tier 2 counts) belongs.
- Add a "Summary" tab: counts of companies by Opportunity Fit, by NAICS Code Type, and by Category, plus a "Top 5 by Suggested Priority Rank" table.

### Step 6 — Job Posting Quick Links tab (skip this step entirely if I said "No" to the Quick Links tab above)

Add a "Job Posting Quick Links" tab — one row per company, with these columns:
- Company
- Job Title Used for Search — the single most likely job title for this company (pull just the first variant out of Suggested Job Title Keywords, not the whole multi-title cell — a focused single-title search works better than one crammed with 3-4 titles at once). If Suggested Job Title Keywords is "N/A" for this company (e.g. a current/internal-only row), use a generic fallback like the industry/purpose keyword instead so the link still works.
- LinkedIn Jobs Search, Indeed Search, Google Jobs Search — three separate HYPERLINK() formulas per row

Use exactly this formula pattern (tested and confirmed working — note the `_xlfn.` prefix on `ENCODEURL`, which Excel requires when this function is written programmatically; omitting it produces a `#NAME?` error), referencing that row's own Company (column A) and Job Title Used for Search (column B) cells on this tab:

```
LinkedIn:    =HYPERLINK("https://www.linkedin.com/jobs/search/?keywords="&_xlfn.ENCODEURL(A2)&"%20"&_xlfn.ENCODEURL(B2),"Search LinkedIn")
Indeed:      =HYPERLINK("https://www.indeed.com/jobs?q="&_xlfn.ENCODEURL(B2)&"+"&_xlfn.ENCODEURL(A2),"Search Indeed")
Google Jobs: =HYPERLINK("https://www.google.com/search?q="&_xlfn.ENCODEURL(A2)&"+"&_xlfn.ENCODEURL(B2)&"+jobs","Search Google Jobs")
```

(Adjust the row number in each formula to match its own row.) These reference this tab's own cells, not the main sheet, so the tab works standalone and the links update automatically if I edit the Company or Job Title cell later.

**Important — be explicit about what this tab is and isn't:** it is a set of pre-built search links, nothing more. Each link just opens LinkedIn, Indeed, or Google with the company name and a job title already typed into the search box — the same as if I'd typed them in myself. Clicking a link does not pull in, list, or embed any actual job postings, and nothing here is "unique jobs found" — it's a shortcut to go run that search, every time, live, whenever I click it. Say this plainly in the file itself (e.g. in the tab's notes or the main Notes tab), not just in your reply.

### Step 6a — Job Post Finder tab (skip this step entirely if I said "No" to the Job Post Finder tab above)

Add a "Job Post Finder" tab — separate from the Job Posting Quick Links tab above, and much simpler: plain reference data, not links or formulas. Exactly two columns:
- Column A: Company Name — same value as the Company column on the main tracker
- Column B: Suggested Job Title Keywords — the full value from the main tracker's Suggested Job Title Keywords column, all 2–4 title variants included, not reduced to a single title

One row per company, same order as the main tracker, header row on row 1. No HYPERLINK() formulas, no job-board-specific columns, nothing clickable — just the two columns side by side. The point is for me to be able to select a company's row, copy the company name and its keyword variants, and paste them into whatever job board or search engine I want to check manually, rather than being limited to the three platforms the Quick Links tab is hardcoded to.

### Step 7 — Industry Events & Forums tab (skip this step entirely if I said "No" to the Events tab above)

Add an "Industry Events & Forums" tab — one row per event, not per company, since the same event is often relevant to several companies on my list at once. Columns:
- Event Name
- Date(s)
- Location
- Format — In-person / Virtual / Hybrid
- Relevant To — reuse the exact values from the main sheet's Category column (not a separate taxonomy), so this tab stays connected to however the companies are already grouped there
- URL

Only include real, currently findable conferences, trade shows, or industry forums relevant to my stated industry/purpose, scoped to how far ahead I specified above. Same honesty standard as everywhere else: only report events actually found via search with a real URL, don't fabricate or guess at an event that "probably exists," and report fewer events rather than padding the list. If coverage for a given Category is thin, say so rather than inventing something to fill the gap.

### Step 8 — Company Activity & Events tab (skip this step entirely if I said "No" to this tab above)

Add a "Company Activity & Events" tab — one row per COMPANY (not per event, unlike the Industry Events tab above), tracking each company's own public activity and event footprint. Columns:
- Company
- Recent LinkedIn Activity — notable posts, announcements, or updates from the window I specified above, with date and a one-line summary
- Podcast / Webcast Appearances — company leadership appearing on a podcast, or the company hosting/participating in a webcast, with date, title, and link
- Upcoming Events / Tradeshows — conferences, tradeshows, or in-person/virtual events this company is attending, sponsoring, or speaking at
- Source URL(s)

This is inherently uneven across companies -- some will have a rich public footprint, many will have little to nothing findable, and that's expected. Same honesty standard as the rest of this request: only report activity verifiable via search with a real, working URL and date. If nothing meaningful turns up for a company, write "No recent public activity found" rather than fabricating a LinkedIn post, podcast appearance, or event that doesn't actually exist.

Format as a clean, formatted Excel workbook with a header row, sensible column widths, and one row per company. Don't fabricate figures — mark clear estimates as such (e.g. "$50M–$250M (estimate)") and leave anything unverifiable blank rather than guessing. If you're confident a company is publicly traded based on your own knowledge, note that as "likely-public (unverified)" rather than implying a filing was directly checked.

---

## Notes

- The M&A research option is off by default and only activates its extra columns when you say Yes — everything else works exactly the same whether you're using this for a job search, sales prospecting, or acquisition research.
- Re-run this same template any time you want to expand — feed it a new company or industry description and ask Claude to add the new rows to your existing tracker instead of starting over.
- Full research is capped at 25 companies, always (see Step 4a) — this is fixed, not a suggestion. Above 25, output automatically splits into a fully-researched Tier 1 and a lighter, basic-info-only Tier 2, rather than thinning out research evenly across everyone.

---

## Step 2 (separate, optional) — LinkedIn Contact Enrichment

This is a genuinely separate follow-up prompt — run it after you already have a tracker and a shortlist, not alongside the request above. Fill in and copy separately.

**Your target companies** *(one per line, 25 or fewer recommended — the easiest source is the Company column from a tracker built above)*
`[Company name(s), one per line]`

**PROMPT (send as-is, with your LinkedIn contacts CSV export attached to the same message)**

Please execute this task directly — match now, rather than describing your plan first or asking permission. I'm attaching a CSV export of my LinkedIn contacts to this message. If you don't have a way to read the attached file, say so plainly and stop rather than guessing at contacts.

Cross-reference my attached LinkedIn contacts CSV against this list of target companies, to help me find warm introduction paths:

*(companies from above)*

For each target company above, check my attached CSV for contacts whose Company/Employer field matches that company — including a clear variant of it (subsidiary, former name, common abbreviation, parent/holding company). For each match found, report:
- Company — from my list above
- Matched Contact Name
- Contact's Title — as listed in the CSV
- Contact's LinkedIn Profile URL — if present in the CSV
- Current or Former — note if the CSV or context suggests this is a past employer for that contact; a former employee can still be a useful warm intro, but it's a different kind of connection than someone there now, so don't blend the two
- Match Confidence — High (exact company name match), Medium (clear variant/subsidiary match), or Low (plausible but uncertain, e.g. a similar name or ambiguous abbreviation)

If a target company has no matching contact in my CSV, still include it in the results with "No match found" rather than omitting it, so I can see coverage across my full list. This only works with what's actually in the file I attached — don't fabricate a contact, and don't guess someone into a company they aren't actually listed against in the CSV.

Format the result as a formatted Excel workbook (.xlsx) — or, if you can't create a file in this context, a clearly organized table in your reply — with one row per matched contact, grouped by company. This is a standalone follow-up step; it doesn't rebuild or modify any tracker from a separate conversation.

**Getting your LinkedIn export, if you haven't already:** Me icon → Settings & Privacy → Data privacy → Get a copy of your data → "Download larger data archive, including connections, verifications, contacts, account history, and information we infer about you based on your profile and activity." Attach the connections CSV directly to the same message as the prompt above.

## A Faster Way to Fill This Out

If you'd rather not fill in the blanks by hand each time, there's a companion tool — `prompt_builder.html` — that gives you the same fields in a live web form and assembles this exact prompt for you as you type, with a one-click copy (or download as .txt if your browser blocks clipboard access). It also lets you save named presets (e.g. "OT Vendors," "Big 4 Consulting") for the current session so you're not retyping your recurring searches. See `Prompt_Builder_User_Guide.md` for how to use it.
