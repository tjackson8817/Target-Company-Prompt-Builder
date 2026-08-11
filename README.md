# Target Company Research Prompt Builder

A free, browser-based tool that turns a form into a detailed, ready-to-paste
prompt for Claude — the prompt asks Claude to research target companies
(via NAICS discovery, named companies, or both) and build a fully
formatted Excel tracker for job search, sales prospecting, partnerships,
or M&A research.

**No installation needed.** Open `prompt_builder.html` in any modern
browser. Fill in what you know, copy or download the generated prompt, and
paste it into a Claude conversation (ideally with web search enabled) to
generate the actual workbook. Nothing you enter is sent anywhere — this
page only builds text locally in your browser.

## How it works

1. Fill in your starting point — company names you already know, an
   industry description, NAICS codes, or all three
2. Optionally narrow the search: exclude specific companies, cap company
   size, or restrict to a ZIP code + radius
3. Describe what the list is for — this is the single most important field,
   since it drives how Claude judges fit, category, and contacts for every
   company
4. Toggle optional add-ons: M&A research columns, a Job Posting Quick Links
   tab, a Job Post Finder tab, an Industry Events & Forums tab, and a
   Company Activity & Events tab
5. Copy or download the generated prompt, paste it into Claude
6. Optionally, run the separate Step 2 prompt to cross-reference your
   LinkedIn contacts export against your top target companies for warm
   introduction paths

## Key features

- **NAICS-based discovery or exact-list enrichment** — either let Claude
  find new candidate companies, or restrict it to only the exact companies
  you name
- **Two-tier output, capped at 25 companies for full research** — if your
  named companies plus any NAICS-discovered candidates exceed 25 total,
  Claude runs a quick qualification pass (named companies get a bonus, but
  aren't automatically guaranteed a slot), gives full research to the
  strongest 25, and puts everyone else in a lighter "Tier 2" list —
  Company, Website, Industry/Sector, and NAICS fit only, sourced from
  efficient batch searches rather than one search per company. Tier 2
  includes a "Promote to Tier 1?" column so you can mark candidates to
  research fully in a follow-up "Just enrich these" run. An optional
  toggle controls whether large, diversified companies (where your
  industry is one product line among many) get included in Tier 2, kept
  in their own clearly separated block if so
- **Company size filter** *(optional)* — e.g. "under 1,000 employees";
  leave blank to include all sizes
- **Location radius filter** *(optional)* — enter a ZIP code and a radius
  in miles (defaults to 100) to restrict results to companies headquartered
  within that distance; leave the ZIP blank for no distance restriction.
  This is separate from the "Preferred location / work arrangement" field,
  which is about your own job-search preferences rather than filtering
  candidate companies by distance
- **M&A research columns** *(optional)* — ownership type, recent M&A
  activity, deal-size fit, and acquisition/acquirer role fit
- **Job Posting Quick Links tab** *(optional, on by default)* — one row per
  company with live HYPERLINK() search links to LinkedIn Jobs, Indeed, and
  Google Jobs
- **Job Post Finder tab** *(optional, on by default)* — a simpler, second
  job-posting-related tab: just Company Name (column A) and the full
  Suggested Job Title Keywords cell (column B), one row per company, no
  formulas or links. Meant for copying a company and its keyword variants
  to paste into whatever job board or search tool you want to check by
  hand, rather than being limited to the three platforms the Quick Links
  tab is hardcoded to
- **Industry Events & Forums tab** *(optional, on by default)* — one row
  per event: real, currently findable conferences and trade shows relevant
  to your stated industry/purpose
- **Company Activity & Events tab** *(optional, off by default)* — one row
  per *company* instead of per event: recent LinkedIn activity, podcast/
  webcast appearances, and upcoming events/tradeshows that specific company
  is attending or speaking at. This is a different, harder research task
  than the Industry Events tab, so it's opt-in and carries an explicit
  "leave it blank rather than fabricate" instruction
- **Templates** — save your current field values under a name and reload
  them later, for scenarios you run repeatedly (session-only; not saved
  across a page reload)
- **Step 2 — LinkedIn Contact Enrichment** *(separate, standalone prompt)* —
  cross-references a LinkedIn contacts export against a shortlist of target
  companies (25 or fewer recommended) to surface warm introduction paths;
  attach your CSV export directly to the chat message, nothing is uploaded
  or parsed by this page itself
- **31 research columns per company** in the main tracker (36 with M&A
  columns on), including a direct careers-page link alongside the website,
  a salary range column pulled from current job postings where one is
  disclosed, growth/hiring signals, opportunity fit, warm introduction
  paths, and (for public companies) named CISO/CIO/CTO disclosures pulled
  from 10-K cybersecurity governance sections and executive compensation
  from proxy statements where applicable

## Files in this repo

| File | Purpose |
|------|---------|
| `prompt_builder.html` | The tool itself — open it in a browser |
| `Target_Company_Research_Prompt_Template.md` | Fill-in-the-blank plain-text alternative to the web form — same fields, same logic, paste directly into Claude |
| `sample_generated_prompt.txt` | Example input: the exact prompt text generated for a real scenario (5 named OT/ICS cybersecurity companies, discovery on, Company Activity tab enabled) — paste this into Claude to see it run |
| `sample_generated_output.xlsx` | Example output: the actual tracker Claude produces from that prompt — real, verified research (not fabricated), demonstrating the two-tier system, all four optional tabs, and full formatting |

## Important notes

- This tool **generates a prompt** — it does not itself call any AI model
  or produce the Excel file. You paste the output into a separate Claude
  conversation to get the actual workbook.
- For best results, use a Claude conversation with **web search enabled**,
  since the generated prompt asks Claude to research real, current
  information (company details, 10-K filings, job postings, industry
  events).
- Company size and location filters are instructions to Claude, not a
  guaranteed hard filter against a live database — Claude applies them
  using its own research judgment, so spot-check a sample of results
  against the filter you specified.
- Full research is capped at 25 companies, always — this is fixed, not a
  suggestion. Above that, the prompt automatically splits output into a
  fully-researched Tier 1 (the strongest 25) and a lighter, basic-info-only
  Tier 2 for everyone else. See the User Guide for the full mechanism,
  including how to promote Tier 2 candidates into a follow-up Tier 1 run.
