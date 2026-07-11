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

**M&A research columns — optional** *(leave this whole section out if not relevant)*
- Add M&A-specific columns? `[Yes / No]`
- If yes, angle: `[Find acquisition targets / Find likely acquirers / Show fit for either]`

---

## PROMPT (send as-is after filling in the section above)

I want you to research target companies and build a formatted Excel tracker (.xlsx). Here's what I have:

- Company/companies I know: *(from above)*
- Industry / field (plain language): *(from above)*
- NAICS code(s) I already know: *(from above)*
- Discovery scope: *(from above)*
- Roughly how many companies per NAICS code: *(from above)*
- Include secondary/adjacent NAICS codes: *(from above)*
- Exclude these companies entirely, even if they'd otherwise match: *(from above, if any)*
- What this list is for: *(from above)*
- Preferred location / work arrangement: *(from above, if any)*
- M&A research angle, if requested above: treat each company accordingly and add the M&A columns described below.

### Step 1 — Confirm or derive the industry/focus label
Use the industry/field description I gave (or infer one from the companies I named) as the label for the "[Industry/Focus Area] Relevance" column below — e.g. if I said "OT Cybersecurity," title that column "OT Cybersecurity Relevance."

### Step 2 — Look up NAICS code(s)
If I didn't give a NAICS code, determine the most appropriate primary code(s) from my industry description or named companies. If "include secondary/adjacent codes" is Yes, also identify relevant secondary/adjacent codes (suppliers, related disciplines).

### Step 3 — Build the candidate company list
For each NAICS code (primary and secondary), generate real, currently-operating companies under that code — a mix of well-known and lesser-known names where possible, prioritizing my stated company-size and location preferences if I gave any. Use the "how many per code" number I gave above as a target (roughly, not a hard cap). Exclude any company I listed in "Exclude these companies." If discovery scope is "Just enrich," skip this step and only use the companies I named directly.

### Step 4 — Research each company and build the Excel tracker
For every company gathered in Step 3 (plus any I named directly), research and build a formatted Excel tracker (.xlsx), one row per company, with these columns:

1. **Company** — legal/common name
2. **Website**
3. **Industry / Sector**
4. **Industry Emphasized** — the specific niche, vertical, or market segment this company emphasizes within that broader sector (e.g. "cloud security for financial services" rather than just "cybersecurity") — gives more market-positioning detail than the sector alone
5. **NAICS Code** — the specific code this company was found under
6. **NAICS Code Type** — Primary or Secondary
7. **Why This NAICS Code** — one line connecting this code back to my starting point (e.g. "Same code as [company I named]" / "Supplier to [industry]" / "Adjacent discipline, different classification")
8. **HQ Location / Footprint** (city, state/country, and whether local, regional, or global)
9. **Company Size** — employee count band
10. **Revenue Band / Latest Revenue** — most recent public figure or reasonable estimate, with source/year noted
11. **Growth / Revenue Signal** — High/Medium/Low plus a brief note on what's driving it
12. **Hiring Signal** — High/Medium/Low plus a brief note, inferred from overall business trajectory (revenue growth, expansion announcements, funding rounds, earnings commentary) and how that connects to my stated purpose — an indirect signal, not a job-posting count
13. **Recent Hiring Trends** — High/Medium/Low based on actual current job postings for this company (check LinkedIn Jobs, Indeed, or the company's own careers page) as of the date this report is run — High = many open roles posted right now, Medium = some open roles, Low = few or no open roles found. This is a direct, concrete snapshot, separate from the broader Hiring Signal above
14. **Opportunity Relevance** — rate High/Medium/Low with a short note on how relevant this company is to my stated purpose, whatever that purpose is (job search, sales, partnerships, M&A, etc.)
15. **Opportunity Fit** — High/Medium/Low, how well this company fits my stated purpose overall
16. **Category** — group companies usefully for my stated purpose (e.g. by NAICS code type, sub-industry, or company role — infer what's most useful)
17. **Why This Fits** — 1–2 sentence rationale connecting the company to my stated purpose
18. **Executive Role Fit** — the level/title most relevant to approach or target at this company for my purpose (e.g. Partner, Managing Director, Practice Lead, VP, Chief Consultant), based on how the company is structured
19. **Warm Introduction Path** — the most plausible path to a warm introduction at this company (e.g. recruiter, executive search firm, former colleagues, LinkedIn 2nd-degree connection, conference/industry contacts), inferred from the company's profile and my background if I've shared it
20. **Outreach Approach** — brief guidance on how and through whom to approach this company
21. **Key Contacts / Priority Titles** — the person/role most relevant to my purpose, named individuals if publicly findable, otherwise closest equivalent titles
22. **Suggested Search Keywords** — terms useful for a LinkedIn or similar search
23. **Source URL** — link(s) supporting the data above
24. **Priority Score** — leave blank for me to fill in
25. **Status** — leave blank (I will fill in: Not Started / Researching / Contacted / In Progress / Closed)
26. **Next Action** — leave blank
27. **Date Researched** — today's date

*(If M&A columns were requested, also add:)*

28. **Ownership Type** — founder-owned, PE-backed, public, subsidiary
29. **Recent M&A Activity**
30. **Signals** — sale/succession signals (if I'm looking for acquisition targets) or acquisition-appetite signals (if I'm looking for acquirers)
31. **Estimated Deal Size Fit**
32. **M&A Role Fit** — Likely Acquisition Target / Likely Acquirer / Could Be Either / Unclear

Format as a clean, formatted Excel workbook with a header row, sensible column widths, and one row per company. Don't fabricate figures — mark clear estimates as such (e.g. "$50M–$250M (estimate)") and leave anything unverifiable blank rather than guessing. If you're confident a company is publicly traded based on your own knowledge, note that as "likely-public (unverified)" rather than implying a filing was directly checked.

---

## Notes

- The M&A research option is off by default and only activates its extra columns when you say Yes — everything else works exactly the same whether you're using this for a job search, sales prospecting, or acquisition research.
- Re-run this same template any time you want to expand — feed it a new company or industry description and ask Claude to add the new rows to your existing tracker instead of starting over.
- No hard limit on total companies, but 15–30 per NAICS code tends to produce the best-researched rows; batch large lists into multiple runs rather than asking for hundreds at once.

## A Faster Way to Fill This Out

If you'd rather not fill in the blanks by hand each time, there's a companion tool — `prompt_builder.html` — that gives you the same fields in a live web form and assembles this exact prompt for you as you type, with a one-click copy (or download as .txt if your browser blocks clipboard access). It also lets you save named presets (e.g. "OT Vendors," "Big 4 Consulting") for the current session so you're not retyping your recurring searches. See `Prompt_Builder_User_Guide.md` for how to use it.
