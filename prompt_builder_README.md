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
   tab, an Industry Events & Forums tab, and a Company Activity & Events tab
5. Copy or download the generated prompt, paste it into Claude

## Key features

- **NAICS-based discovery or exact-list enrichment** — either let Claude
  find new candidate companies, or restrict it to only the exact companies
  you name
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
- **28-29 research columns per company** in the main tracker, including
  growth/hiring signals, opportunity fit, warm introduction paths, and (for
  public companies) named CISO/CIO/CTO disclosures pulled from 10-K
  cybersecurity governance sections and executive compensation from proxy
  statements where applicable

## Files in this repo

| File | Purpose |
|------|---------|
| `prompt_builder.html` | The tool itself — open it in a browser |
| `sample_generated_prompt.txt` | Example output: the exact prompt text generated from a filled-in scenario (OT/ICS consulting prospects, size- and location-filtered, with the Company Activity tab enabled) |

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
- Totals above roughly 50-75 companies in one prompt tend to come back with
  thinner research per company — batch larger requests into multiple
  prompts if you need more.
