# Target Company Research → Excel Tracker
### Reusable Prompt Template (Section 2: Full Research Tracker)

Copy everything below into a new Claude chat. Fill in the fields at the top, delete anything you don't need, and send it. Works for any purpose — job search, sales prospecting, partnership scouting, investment research, vendor evaluation, etc.

**This template covers Section 2 of the tool only.** If you want a wide, cheap candidate list to prune by hand first (Section 1 — Bulk Company Pull) or the standalone LinkedIn contact-matching step (Section 3), those don't have a plain-text template yet — use the web form (`prompt_builder.html`) for those, or ask Claude directly to build one from this file as a starting point.

---

## FILL THIS IN

**Starting point** *(fill in whichever of these you actually have — one is enough, use as many as apply)*

- **Company(s) you know** (current employer, former employer, a competitor, anyone): `[Company name(s), or leave blank]`
- **Industry / field, in plain language** (no jargon needed — be specific, since this phrase is used to derive NAICS codes later): `[e.g. "industrial cybersecurity consulting" / "commercial HVAC controls" / "specialty coffee roasting" — or leave blank]`
- **NAICS code(s), if you already happen to know them:** `[leave blank if unknown — Claude will infer per-company codes later]`

**Exclude these companies** *(optional — leave out entirely even if they'd otherwise match)*
`[Company name(s), or leave blank]`

**Limit to company size — optional** *(e.g. "under 1,000 employees" — leave blank to include all sizes)*
`[Size filter, or leave blank]`

**Limit to a location radius — optional** *(enter a ZIP code and a radius to restrict results to companies headquartered within that distance; leave the ZIP blank for no distance restriction — separate from "Preferred location / work arrangement" below, which is about your own preferences, not a company-distance filter)*
`[ZIP code, or leave blank]`
`[Radius in miles — default 100 if a ZIP is given]`

**Discovery Scope** *(this controls what Claude actually does with the above)*
`[Find new companies / Just enrich the companies I listed — default: Find new companies]`

**Roughly how many candidates to gather during discovery — optional**
`[e.g. 15–30 — or leave blank for Claude's judgment]`

**Include secondary/adjacent NAICS codes on each company?** *(broadens each company's classification tagging to include supplier/vendor/related-industry codes — this doesn't change how companies are found, only how they're tagged)*
`[Yes / No — default Yes if left blank]`

**Use a two-tier target list? — optional** *(only meaningful if Discovery Scope above is "Find new companies" — ignored otherwise, since there's no discovered pool to rank in enrich-only mode)*
`[Yes / No — default No if left blank]`
`If yes — Tier 1 size (full detail): [default 25]`
`If yes — Tier 2 size (lighter detail): [default 75]`

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

**Add a Job Post Finder tab?** *(simpler companion tab: just Company Name and the full Suggested Job Title Keywords cell, no formulas or links — for pasting into whatever job board you actually want to use)*
`[Yes / No — default Yes if left blank]`

**Add an Outreach Contacts tab?** *(Company, Key Contacts / Priority Titles, Warm Introduction Path, and Category side by side — formatted for pasting into the companion Outreach Message Builder tool's bulk-paste box)*
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
- Roughly how many candidates to gather during discovery: *(from above)*
- Include secondary/adjacent NAICS codes on each company: *(from above)*
- Exclude these companies entirely, even if they'd otherwise match: *(from above, if any)*
- Company size filter, if given above: only include companies matching that size band — exclude companies outside it.
- Location filter, if a ZIP was given above: only include companies headquartered within the given radius of that ZIP code. Estimate the distance from each company's HQ to the ZIP code and note the approximate mileage as part of the HQ Location / Footprint column.
- What this list is for: *(from above)*
- Preferred location / work arrangement: *(from above, if any)*
- My background, if I shared it above: use it to sharpen Suggested Job Title Keywords and Warm Introduction Path — look for former-employer overlap, transferable experience, or relevant credentials.
- M&A research angle, if requested above: treat each company accordingly and add the M&A columns described below.

### Step 1 — How to discover new companies (only relevant if Discovery scope is "Find new companies")

Do NOT rely on NAICS codes as the search mechanism — a code alone is far too broad to use as a filter (it would return any IT/consulting business in North America), and there is no bulk, robots-allowed public source that returns "every company under code X" (SAM.gov's search blocks automated access; Census.gov has no company directory, only code definitions). Instead, discover companies via:

1. **Competitor/alternative cascade** — for each company I named above, search "[company] competitors" and "[company] alternatives," and repeat outward for companies you find this way too.
2. **Analyst & category sources** — Gartner Magic Quadrant / Forrester Wave entries, G2/Capterra category pages, or equivalent category-leader lists relevant to this space.
3. **Conference exhibitor/sponsor lists** — relevant industry conferences and trade shows often publish exhibitor or sponsor lists, a strong signal for "real company actively in this space."
4. **Live job-posting search** — searching for the kind of role tied to my industry/purpose surfaces companies actively hiring in this space.

If discovery scope is "Just enrich," skip this step entirely and only use the companies I named directly.

### Step 2 — NAICS classification (applies to every company, named or discovered)

For each company, identify up to 5 NAICS codes total: 1 primary code (the closest single match to its dominant service line) plus up to 4 secondary/adjacent codes if I said Yes to including them above. State which keyword or phrase from my industry/company description you used to derive these codes, so I can catch a bad extraction rather than it silently propagating through the list. Use these codes to sanity-check that a company the cascade surfaced is actually in-category, not a false-positive adjacent business.

### Step 3 — Research each company and build the Excel tracker

For every company gathered above, research and build a formatted Excel tracker (.xlsx), one row per company, with these columns:

1. **Company** — legal/common name
2. **Website**
3. **Careers Page** — a direct link to this company's careers/jobs listing page specifically (e.g. "acme.com/careers" or their Workday/Greenhouse/Lever posting board), not just the homepage. Leave blank if you can't find one rather than guessing at a URL pattern
4. **Industry / Sector**
5. **Industry Emphasized** — the specific niche, vertical, or market segment this company emphasizes within that broader sector (e.g. "cloud security for financial services" rather than just "cybersecurity") — gives more market-positioning detail than the sector alone
6. **NAICS Code(s)** — up to 5 total, from Step 2, primary first
7. **NAICS Code Type** — Primary or Secondary, for the first/lead code listed
8. **Why This NAICS Code** — one line connecting the code(s) back to my starting point, including the keyword/phrase used to derive them
9. **HQ Location / Footprint** (city, state/country, and whether local, regional, or global)
10. **Company Size** — employee count band
11. **Revenue Band / Latest Revenue** — most recent public figure or reasonable estimate, with source/year noted
12. **Growth / Revenue Signal** — High/Medium/Low plus a brief note on what's driving it
13. **Hiring Signal** — High/Medium/Low plus a brief note, inferred from overall business trajectory (revenue growth, expansion announcements, funding rounds, earnings commentary) and how that connects to my stated purpose — an indirect signal, not a job-posting count
14. **Recent Hiring Trends** — High/Medium/Low based on actual current job postings for this company (check LinkedIn Jobs, Indeed, or the company's own careers page) as of the date this report is run — High = many open roles posted right now, Medium = some open roles, Low = few or no open roles found. This is a direct, concrete snapshot, separate from the broader Hiring Signal above
15. **Salary Range (if posted)** — while checking job postings for the Recent Hiring Trends column above, note the salary range if any posting discloses one, along with the job title it's attached to (e.g. "$140K-$170K — Sr. OT Security Engineer posting"). Leave blank if no posting discloses a range — don't estimate or infer a figure
16. **Opportunity Relevance** — rate High/Medium/Low with a short note on how relevant this company is to my stated purpose, whatever that purpose is (job search, sales, partnerships, M&A, etc.)
17. **Opportunity Fit** — High/Medium/Low, how well this company fits my stated purpose overall
18. **Category** — group companies usefully for my stated purpose
19. **Why This Fits** — 1–2 sentence rationale connecting the company to my stated purpose
20. **Executive Role Fit** — the level/title most relevant to approach or target at this company for my purpose (e.g. Partner, Managing Director, Practice Lead, VP, Chief Consultant), based on how the company is structured
21. **Warm Introduction Path** — the most plausible path to a warm introduction at this company (e.g. recruiter, executive search firm, former colleagues, LinkedIn 2nd-degree connection, conference/industry contacts), inferred from the company's profile and my background if I've shared it
22. **Outreach Approach** — brief guidance on how and through whom to approach this company
23. **Key Contacts / Priority Titles** — named individuals if publicly findable, otherwise closest equivalent titles. Additionally, for publicly traded companies only, check the most recent 10-K's cybersecurity governance disclosure (Item 1C / Regulation S-K Item 106) for a named CISO, CIO, CTO, or similarly responsible officer. If found, add as a clearly labeled second line: "(per FY20XX 10-K)". If the company is public but no one is named, say so briefly rather than omitting silently. If the company is privately held with no 10-K, skip this entirely.
24. **Compensation Benchmark** — for publicly traded companies only: if the individual named from the 10-K in column 23 also appears in that company's most recent proxy statement (DEF 14A) Summary Compensation Table as a Named Executive Officer, report their total compensation figure with the fiscal year noted. When it doesn't apply, say so briefly ("not a Named Executive Officer — not disclosed") rather than leaving the cell ambiguously blank. Skip entirely for private companies.
25. **Suggested Search Keywords** — terms useful for a LinkedIn people-search
26. **Suggested Job Title Keywords** — 2–4 actual job title variants this specific company would plausibly use in a job posting for the Executive Role Fit identified above, informed by my background where relevant
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

### Step 4 — Two-tier output (only if I said Yes to "Use a two-tier target list?" above, AND Discovery scope is "Find new companies")

If either condition isn't met, skip this step — output a single tracker with full research (Step 3's columns) on everyone.

If both conditions are met: rank the full discovered pool against my stated purpose. The top *(Tier 1 size from above)* companies become **Tier 1** and get the full column set from Step 3. The next *(Tier 2 size from above)* companies become **Tier 2** and get only this shorter set — skip careers-page verification, job-posting/hiring checks, salary data, 10-K/proxy research, named contacts, and keyword generation:

1. Company
2. Website
3. Industry / Sector
4. NAICS Code(s) — up to 5, primary first
5. NAICS Code Type
6. HQ Location / Footprint
7. Company Size — best available estimate
8. Opportunity Fit — High/Medium/Low only, no rationale needed
9. Category — same grouping logic as Tier 1
10. Source URL

Put Tier 1 in a tab named "Tier 1 - Priority Targets" and Tier 2 in a separate tab named "Tier 2 - Extended List" (plain data, autofilter fine, but skip the rating-color gradient and Suggested Priority Rank formula since Tier 2 doesn't have the underlying rating columns). Any tabs below that pull from "the main tracker" should pull from Tier 1 only.

### Step 5 — Formatting (skip this step entirely if I said "No" to visual formatting above)

Apply all of the following to the Excel file:
- Color-code these five rating columns using a 5-step gradient keyed to the leading word of each cell: Growth / Revenue Signal, Hiring Signal, Recent Hiring Trends, Opportunity Relevance, Opportunity Fit. Very High = darker green (A9D8A9), High = green (C6E8C6), Medium-High = yellow-green (E2EFC0), Medium = yellow (FFF2B2), Low-Medium = orange (FBDCB8), Low = red (F4C7C3).
- Add a "Suggested Priority Rank (1-25)" column positioned immediately next to the blank Priority Score column. Compute it per company: convert each rating word to points (Very High=5, High=4, Medium-High=3.5, Medium=3, Low-Medium=2, Low=1), then score = (Opportunity Fit points x 2) + (Opportunity Relevance points x 2) + average(Growth/Revenue Signal points, Hiring Signal points, Recent Hiring Trends points). Round to 1 decimal. Color this column using the same gradient, bucketed by score: ≥22 Very High, ≥18 High, ≥14 Medium-High, ≥10 Medium, ≥7 Low-Medium, else Low. Add a cell comment on this column's header noting it's a mechanical starting point, not a replacement for my own judgment.
- Hyperlink the Website and Careers Page columns so each cell links to that company's actual site/careers page. Leave Source URL as plain text.
- Add autofilter on the header row. Freeze both the header row and the Company column.
- Lightly shade alternating data rows (zebra striping), without overriding the rating-column colors above.
- Give the Priority Score, Status, and Next Action columns a distinct light fill and border, separate from the rating gradient.
- Add a "Notes & Assumptions" tab: document which figures are verified vs. estimated, list key assumptions, and include a color legend explaining the gradient above.
- Add a "Summary" tab: counts of companies by Opportunity Fit, by NAICS Code Type, and by Category, plus a "Top 5 by Suggested Priority Rank" table.

### Step 6 — Job Posting Quick Links tab (skip if I said "No" above)

Add a "Job Posting Quick Links" tab — one row per company, with these columns:
- Company
- Job Title Used for Search — the single most likely job title for this company (pull just the first variant out of Suggested Job Title Keywords). If Suggested Job Title Keywords is "N/A," use a generic fallback like the industry/purpose keyword.
- LinkedIn Jobs Search, Indeed Search, Google Jobs Search — three separate HYPERLINK() formulas per row

Use exactly this formula pattern (note the `_xlfn.` prefix on `ENCODEURL`, required when written programmatically):

```
LinkedIn:    =HYPERLINK("https://www.linkedin.com/jobs/search/?keywords="&_xlfn.ENCODEURL(A2)&"%20"&_xlfn.ENCODEURL(B2),"Search LinkedIn")
Indeed:      =HYPERLINK("https://www.indeed.com/jobs?q="&_xlfn.ENCODEURL(B2)&"+"&_xlfn.ENCODEURL(A2),"Search Indeed")
Google Jobs: =HYPERLINK("https://www.google.com/search?q="&_xlfn.ENCODEURL(A2)&"+"&_xlfn.ENCODEURL(B2)&"+jobs","Search Google Jobs")
```

This tab is a set of pre-built search links, nothing more — clicking one just opens a live search, exactly as if I'd typed it myself. Say this plainly in the file itself.

### Step 6a — Job Post Finder tab (skip if I said "No" above)

Add a "Job Post Finder" tab — plain reference data, not links or formulas. Exactly two columns: Company Name, and the full Suggested Job Title Keywords cell (all variants, not reduced to one). One row per company, no formulas, nothing clickable.

### Step 6b — Outreach Contacts tab (skip if I said "No" above)

Add an "Outreach Contacts" tab — plain reference data, not links or formulas, feeding a separate companion tool (Outreach Message Builder). Exactly four columns, in this exact order: Company, Key Contacts / Priority Titles, Warm Introduction Path, Category. One row per company, same order as the main tracker. These four columns aren't adjacent on the main sheet, so this tab exists purely to put them side by side for a clean copy-paste.

### Step 7 — Industry Events & Forums tab (skip if I said "No" above)

Add an "Industry Events & Forums" tab — one row per event, not per company. Columns: Event Name, Date(s), Location, Format (In-person/Virtual/Hybrid), Relevant To (reuse the main sheet's Category values), URL. Only real, currently findable events with a real URL, scoped to the window I specified. Report fewer events rather than padding the list.

### Step 8 — Company Activity & Events tab (skip if I said "No" above)

Add a "Company Activity & Events" tab — one row per COMPANY. Columns: Company, Recent LinkedIn Activity, Podcast / Webcast Appearances, Upcoming Events / Tradeshows, Source URL(s). Check each company from a few different angles (its own LinkedIn page, podcast/webinar search, conference search) before concluding there's nothing. If nothing meaningful turns up, write "No recent public activity found" rather than fabricating anything.

Format the result as a clean, formatted Excel workbook with a header row, sensible column widths, and one row per company. Don't fabricate figures — mark clear estimates as such and leave anything unverifiable blank rather than guessing.

---

## Notes

- The M&A research option is off by default and only activates its extra columns when you say Yes.
- Re-run this same template any time you want to expand — feed it a new company or industry description and ask Claude to add new rows to your existing tracker instead of starting over.
- There's no automatic company cap. Totals above roughly 50–75 companies in one run tend to come back thinner per company — use the two-tier option above, or the web tool's Section 1 (Bulk Company Pull) for a wider, cheaper first pass to prune by hand.

---

## Section 3 (separate, optional) — LinkedIn Contact Enrichment

This is a genuinely separate follow-up prompt — run it after you already have a tracker and a shortlist, not alongside the request above. Fill in and copy separately.

**Your target companies** *(one per line, 25 or fewer recommended — the easiest source is the Company column from a tracker built above)*
`[Company name(s), one per line]`

**PROMPT (send as-is, with your LinkedIn contacts CSV export attached to the same message)**

Please execute this task directly — match now, rather than describing your plan first or asking permission. I'm attaching a CSV export of my LinkedIn contacts to this message. If you don't have a way to read the attached file, say so plainly and stop rather than guessing at contacts.

Cross-reference my attached LinkedIn contacts CSV against this list of target companies, to help me find warm introduction paths:

*(list your target companies here, one per line)*

For each target company above, check my attached CSV for contacts whose Company/Employer field matches that company — including a clear variant of it (subsidiary, former name, common abbreviation, parent/holding company). For each match found, report: Company, Matched Contact Name, Contact's Title, Contact's LinkedIn Profile URL (if present), Current or Former status, and Match Confidence (High/Medium/Low). If a target company has no matching contact, still include it as "No match found" rather than omitting it. Format the result as a formatted Excel workbook (.xlsx) — or a clearly organized table in your reply if you can't create a file — with one row per matched contact, grouped by company.
