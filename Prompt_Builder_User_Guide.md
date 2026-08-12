**SALE FISH**

MARKETING AND CONSULTING

# Target Company Research Prompt Builder

User Guide

**Live Tool:** [https://tjackson8817.github.io/Target-Company-Prompt-Builder/](https://tjackson8817.github.io/Target-Company-Prompt-Builder/)

Created By: Tom Jackson
Updated: August 11, 2026 — v3 (adds Section 1 Bulk Company Pull; discovery method changed from NAICS-based search to competitor-cascade; see "What Changed in v3" below)

## About This Tool & Cross-Platform Compatibility

### Built for Claude

The Target Company Prompt Builder was designed, built, and tested for use with Claude (Anthropic). The prompts it generates are written to match how Claude interprets instructions, structures research, and formats output — including building formatted .xlsx trackers directly in the conversation.

### Using the Output Prompts with Other AI Tools

Every prompt this tool generates is plain text, so none of them are locked to Claude — you're free to paste them into other generative AI apps (ChatGPT, Gemini, Copilot, etc.). A few things to expect if you do:

- Some apps will run it as-is and return comparable results.
- Some may need minor edits — for example, a tool without built-in spreadsheet-creation ability might return the same research as a formatted table or CSV text instead of a downloadable .xlsx file.
- Some may offer their own suggestions for how to restructure or run the prompt based on that platform's particular strengths or limitations.

One concrete example worth knowing: in ChatGPT, web browsing and Code Interpreter (its file-building tool) are separate capabilities, and the Code Interpreter sandbox has no internet access. That means a single unified pass — live research and a live-built Excel file in the same response — isn't guaranteed the way it is in a Claude session with both Web search and Code execution and file creation enabled. Expect either a plain-text/table result, or a two-step process.

None of this means a prompt is broken elsewhere — it just means results, formatting, and follow-up behavior may vary by platform.

### The Overall Goal

However you run it, the goal of this tool stays the same: make it easy to enter your key target-company attributes — a company you know, an industry, a NAICS code, your purpose — and generate a clear, complete prompt that's easy for you to read, edit, and adapt before you run it anywhere.

### What Changed in v3

If you used an earlier version of this tool, three things are different:

- **New: Section 1 — Bulk Company Pull.** A separate, cheap, wide-net prompt that turns a small seed list into a large flat list of candidate companies for you to prune by hand — see Section 3 of this guide.
- **Discovery method changed.** Earlier versions framed NAICS codes as the way Claude finds new companies. That didn't hold up in practice — a NAICS code alone is too broad to search by, and the one government source that can filter companies by code (SAM.gov) blocks automated access. Discovery is now driven by a competitor cascade, analyst/category sources, conference exhibitor lists, and live job-posting search — with NAICS demoted to a supporting classification tag (up to 5 codes per company) rather than the discovery engine. See Section 5.
- **Tiering is now a manual, adjustable toggle**, not an automatic 25-company cap. You choose Tier 1 and Tier 2 sizes yourself, and tiering only takes effect when Discovery scope is "Find new companies" — it's ignored in "Just enrich these" mode, since there's no discovered pool to rank in that mode. See Section 8.

## Claude Settings You'll Need Before You Start

These prompts ask Claude to do two things: research live, and build a real .xlsx file. Both depend on settings that aren't always on by default.

| Setting | Why you need it / Where to find it |
|---|---|
| Web search | Without it, Claude can't do the actual live company research these prompts depend on. Click the + (or slider) icon in the chat input, find Web search, toggle it on. |
| Code execution and file creation | This is what lets Claude build and hand you a downloadable .xlsx. Settings → Capabilities, toggle it on. |

## 1. Opening the Tool

- Locate prompt_builder.html (wherever your browser saved it) or open the live hosted version, which needs no download at all.
- Double-click it. It opens in your default browser like any web page.
- If it opens as plain text/code instead of a working page, right-click the file → Open with → choose your browser explicitly.

Nothing is sent anywhere when you use this — it's just a form that builds text, entirely on your own machine.

## 2. How the Page Is Organized

The tool is one page, top to bottom, in four parts:

1. **Shared Inputs** — the fields every other section reads from (companies you know, industry, NAICS, exclusions, size/location filters).
2. **Section 1 — Bulk Company Pull** (optional) — a fast, wide, low-detail discovery prompt you run first if you want a large candidate list to prune by hand.
3. **Section 2 — Full Research Tracker** — the main tool: scope, purpose, tiering, formatting, and optional tabs, producing the full research prompt.
4. **Section 3 — LinkedIn Contact Enrichment** (optional) — a separate, self-contained prompt that cross-references a LinkedIn export against a company shortlist.

Sections 1, 2, and 3 each have their own Copy prompt / Download .txt buttons and their own output panel — they are three separate prompts meant to be run as separate Claude conversations (or separate messages), not one combined prompt.

## 3. Shared Inputs

You only need one of these filled in — fill in more than one if you have them, and the tool will combine them.

| Field | What to put in it |
|---|---|
| Company(s) you know | A current employer, former employer, competitor — any real company name(s), one per line or comma-separated. A live hint tracks how many you've listed: 5-10 tends to give the cleanest results, past 20 the discovery cascade runs noticeably slower, and past 50 the tool suggests Anthropic's dedicated Research feature instead |
| Industry / field, plain language | A description in your own words — no jargon needed (e.g. "commercial HVAC controls"). Be specific — see the note on NAICS extraction below. Not sure how to phrase it? The field links directly to the [Census NAICS Search](https://www.census.gov/naics/) so you can borrow official industry wording without needing to know your own code |
| NAICS code(s), if known | Skip this if you don't know it — Claude will infer one per company later in the process |

There's also an **Exclude these companies** field (optional) — anything you list there is left out entirely, even if it would otherwise match.

Two more optional narrowing fields: **Limit to company size** (e.g. "under 1,000 employees") and **Limit to a location radius** (a ZIP code plus a radius in miles, default 100) — both are instructions to Claude's research judgment, not a guaranteed hard filter against a live database.

**A note on NAICS codes in this tool.** NAICS (North American Industry Classification System) is the standard the U.S. and Canadian governments use to categorize industries. It's useful here as a *classification tag* on each company — up to 5 codes per company (1 primary + up to 4 secondary), stated alongside the keyword/phrase used to derive them so you can catch a bad extraction. It is **not** used to discover new companies in bulk: a code alone is too broad to search by (it would return any IT/consulting business in North America), and the one government source that lets you filter companies by NAICS code — SAM.gov's entity search — blocks automated access. See Section 5 for how discovery actually works.

## 4. Section 1 — Bulk Company Pull (Optional)

A separate, cheap prompt for building a wide candidate list fast, before you commit to full research on anyone. Skip this section entirely if you already know exactly which companies you want researched — go straight to Section 2 with Discovery scope set to "Just enrich these."

**What it asks Claude for:** a flat list of candidate companies using your Shared Inputs as seeds, with only five columns per company — no deep verification, no per-company career-page/job-posting/filing checks:

1. Company
2. Website
3. Inferred NAICS Code — single best guess, or blank if Claude can't confidently guess one
4. What They Do — one line
5. Source — the search/page that surfaced this company, so you can spot-check quality

**Target list size** (default 75-100) — since there's no per-company research cost here, this can go wider than Section 2's practical ceiling. Claude is instructed to say so and give you fewer companies rather than pad the list if your seed/industry genuinely can't support the target size.

**Discovery method** — the same one used in Section 2 (see Section 5): competitor/alternative cascade, analyst and category sources, conference exhibitor lists, and live job-posting search. NAICS codes are applied as a tag after the fact, not used as a search filter.

**What to do with the result:** open the .xlsx Claude builds, delete the rows that aren't relevant, then copy just the **Company** column from what's left. That's the only column Section 2 actually reads back in — paste those names into "Company(s) you know" in Shared Inputs, then set Section 2's Discovery scope to "Just enrich these" so the full research pass only spends effort on companies you've already vetted.

## 5. How Discovery Actually Works

This applies to both Section 1 and Section 2 whenever new companies are being found (Section 1 always does this; Section 2 does it only when Discovery scope is "Find new companies"):

1. **Competitor/alternative cascade** — for each seed company you named, Claude searches "[company] competitors" and "[company] alternatives," and repeats outward for companies it finds that way too.
2. **Analyst & category sources** — Gartner Magic Quadrant / Forrester Wave entries, G2/Capterra category pages, or equivalent category-leader lists for your space.
3. **Conference exhibitor/sponsor lists** — industry conferences and trade shows often publish exhibitor or sponsor lists, a strong signal for "real company actively in this space."
4. **Live job-posting search** — searching for the kind of role tied to your industry/purpose surfaces companies actively hiring in that space, doubling as a real hiring-signal data point.

NAICS codes are applied to each company *after* it's found this way — a tag for classification and light sanity-checking, not the search mechanism. If Claude has live access to a NAICS-filterable data source that's actually queryable (the free, public USASpending.gov API is one example — unlike SAM.gov's blocked search UI, it returns real federal-contract-recipient company names filtered by NAICS code), it may use that as one more discovery channel, but it only covers companies with a federal-contracting footprint and will miss most private-sector-only firms.

## 6. Section 2 — Full Research Tracker: Scope & Purpose Fields

| Field | What it does |
|---|---|
| Discovery scope | "Find new companies" = Claude does its own moderate discovery (the method in Section 5) bundled into the full research pass. "Just enrich these" = Claude only researches the exact company names you typed — no new companies added. Switching to "Just enrich these" also hides the three fields below it (candidate count, secondary NAICS codes, two-tier toggle) since none of them apply without a discovery pass to act on. |
| Roughly how many companies to find | A loose volume dial for this discovery pass — the Section 2 equivalent of Section 1's "Target list size." Unlike Section 1, every company found here gets full research, so totals above ~50–75 tend to come back thinner per company. Only visible when Discovery scope is "Find new companies." |
| Include secondary/adjacent NAICS codes? | "Yes" (default) broadens each company's NAICS tagging to include supplier/vendor/related-industry codes. "No" keeps tagging tightly scoped to the primary code only. |
| Use a two-tier target list? | See Section 8. Only takes effect when Discovery scope is "Find new companies." |
| What is this list for? | The most important field — it tells Claude how to judge fit, category, and contacts for every company. |
| Preferred location / work arrangement | Optional. Adds a column rating each company against this preference. |
| Your background | Optional. Paste resume/CV/bio text directly. Sharpens Suggested Job Title Keywords and Warm Introduction Path. |
| Include full visual formatting in the tracker? | "Yes" (default) bakes color-coding, Suggested Priority Rank, hyperlinks, autofilter, and Notes/Summary tabs into the prompt itself. |
| Add a Job Posting Quick Links tab? | "Yes" (default) adds pre-built LinkedIn/Indeed/Google Jobs search links per company. See Section 13. |
| Add a Job Post Finder tab? | "Yes" (default) adds a simpler Company + full Suggested Job Title Keywords reference tab. See Section 14. |
| Add an Outreach Contacts tab? | "Yes" (default) adds a four-column reference tab (Company, Key Contacts / Priority Titles, Warm Introduction Path, Category) formatted for pasting straight into the companion Outreach Message Builder tool. See Section 14a. |
| Add an Industry Events & Forums tab? | "Yes" (default) adds real, upcoming events relevant to your industry. See Section 15. |
| Add a Company Activity & Events tab? | "No" by default — a harder research task, one row per company. See Section 16. |
| Add M&A-specific columns? | See Section 7. |

## 7. M&A Research Columns (Optional)

A separate fieldset lets you turn on M&A-specific columns for any list.

- Set Add M&A-specific columns? to Yes. A second option — M&A angle — appears.
- **Find acquisition targets** — you're the buyer.
- **Find likely acquirers** — you want to know who might buy a company like yours.
- **Show fit for either** — rates each company both ways.

This adds Ownership Type, Recent M&A Activity, a Signals column, Estimated Deal Size Fit, and M&A Role Fit.

*Honest limits: these columns only draw on public information — news, filings, press releases. Claude is instructed not to treat silence as evidence a company isn't open to a deal.*

## 8. The Two-Tier Output System

Off by default, and now fully manual — this replaced an earlier automatic 25-company cap.

**When it's active.** Only when both of these are true: Discovery scope is "Find new companies," **and** Use a two-tier target list? is set to Yes. The tiering toggle and its Tier 1/Tier 2 size fields are hidden entirely whenever Discovery scope is "Just enrich these," so this shouldn't come up in normal use — but the underlying rule holds regardless: in every other case, including if a saved template carries a leftover tiered=Yes value, you get one flat tracker with full research on everyone, and no Tier 2 tab logic runs at all.

**Tier 1 size / Tier 2 size.** Two plain number fields (defaults 25 and 75) — you set them directly, there's no automatic qualification pass, no dedup logic, and no ranking bonus for named companies baked into the mechanism. Claude ranks the discovered pool against your stated purpose and puts the top N (Tier 1 size) in full research; the next N (Tier 2 size) get a lighter pass.

**Tier 1 columns.** The full column set in Section 11.

**Tier 2 columns.** Exactly ten: Company, Website, Industry / Sector, NAICS Code(s), NAICS Code Type, HQ Location / Footprint, Company Size, Opportunity Fit, Category, Source URL. No revenue, no hiring signals, no contacts, no careers-page verification.

**Output structure.** Two tabs — "Tier 1 - Priority Targets" and "Tier 2 - Extended List." Tabs that depend on Tier-1-only columns (Job Posting Quick Links, Job Post Finder, Outreach Contacts) pull from Tier 1 only.

**Closing the loop.** If you want a Tier 2 company researched at full depth, copy its name and run the tool again with Discovery scope set to Just enrich these.

## 9. Reading the Live Prompt Panels

Each of the three sections' output panels updates instantly as you type — there's no "Generate" button.

- Copy prompt copies that section's prompt to your clipboard.
- If your browser blocks clipboard access, click Download .txt instead.
- Paste it into a new Claude chat and send it as-is.

## 10. Saving and Reusing Templates

- Fill in the form the way you want it.
- Type a name in Template name and click Save current as template.
- Later, pick it from the dropdown and click Load.
- Delete removes a template you no longer need.

*Templates only persist for the current browser tab/session — they are not written to a file or account. Saved fields include Section 1's target list size and Section 2's tier sizes.*

## 11. Typical Workflow, Start to Finish

- Open prompt_builder.html.
- Fill in Shared Inputs.
- **Wide net first?** Run Section 1, prune the result down to the companies you actually want, and paste the survivors' Company column back into Shared Inputs.
- Set Section 2's Discovery scope to "Just enrich these" if you used Section 1, or "Find new companies" if you're skipping straight to a modest, bundled discovery pass.
- Set purpose, tiering (if using Find new companies), and any optional tabs or M&A columns.
- Copy the Section 2 prompt and paste it into a new Claude chat.
- Download the .xlsx tracker Claude produces.
- If you want a follow-up on any Tier 2 company, copy its name and re-run in "Just enrich these" mode.

## 12. Quick Troubleshooting

| Problem | Fix |
|---|---|
| The file opens as code/text instead of a page | Right-click → Open with → your browser |
| "Copy prompt" doesn't seem to do anything | Some browsers silently block clipboard access — use Download .txt instead |
| A prompt panel just shows placeholder text | You need at least one Shared Input field filled in (Section 1 and 2) or a companies list (Section 3) |
| Saved templates disappeared | Templates only last for the current browser tab/session |
| Tiering didn't apply even though the checkbox says Yes | Check Discovery scope — tiering only activates in "Find new companies" mode (Section 8) |
| Output rows feel thin/generic | If tiering is active, check whether a company landed in Tier 2 — that tab is basic-info-only by design, not a research shortfall |

## 13. What's in the Output Tracker

The prompt asks Claude to research and fill in these 31 columns for every Tier 1 (or single-tier) company, 36 with M&A columns on:

Company, Website, Careers Page, Industry / Sector, Industry Emphasized, NAICS Code(s), NAICS Code Type, Why This NAICS Code, HQ Location / Footprint, Company Size, Revenue Band / Latest Revenue, Growth / Revenue Signal, Hiring Signal, Recent Hiring Trends, Salary Range (if posted), Opportunity Relevance, Opportunity Fit, Category, Why This Fits, Executive Role Fit, Warm Introduction Path, Outreach Approach, Key Contacts / Priority Titles, Compensation Benchmark, Suggested Search Keywords, Suggested Job Title Keywords, Source URL, Priority Score, Status, Next Action, and Date Researched — plus a formula-computed Suggested Priority Rank column (see Section 14).

**Additions worth knowing about specifically**

- **NAICS Code(s)** now holds up to 5 codes per company (primary first), and **Why This NAICS Code** states the keyword used to derive them — see Section 3.
- **Careers Page** sits right next to Website — the company's own jobs/careers listing page specifically, not the homepage.
- **Industry Emphasized** adds the market-positioning detail a broad sector label misses.
- **Salary Range (if posted)** rides along with the Recent Hiring Trends check — reported only when a posting actually discloses one.
- **Hiring Signal** vs **Recent Hiring Trends**: the first is inferred from business trajectory, the second is a direct, concrete snapshot of current job postings.
- **Opportunity Relevance** is deliberately generic, so the same tool works for a job search, sales prospecting, or M&A.
- **Suggested Search Keywords** finds people; **Suggested Job Title Keywords** finds postings — tailored per company.
- **Key Contacts / Priority Titles** can carry a second line for public companies — a named cybersecurity executive sourced from the 10-K. See Section 17.

## 14. Reading the Formatted Tracker

- **Color-coded ratings.** Five rating columns shaded on a 5-step gradient, green (High) to red (Low). Legend on the Notes & Assumptions tab.
- **Suggested Priority Rank (1-25).** A mechanical starting point next to the blank Priority Score column, computed by formula from the five rating columns — compare the two and overrule where you disagree.
- **Website and Careers Page are clickable.** Source URL stays plain text on purpose.
- **Autofilter and frozen panes** on the header row and Company column.
- **Zebra striping** on alternating rows.
- **Priority Score, Status, and Next Action** get a distinct pale-yellow fill — your inputs, visually separate from Claude's research.
- **A Summary tab** with counts by Opportunity Fit, NAICS Code Type, and Category, plus a Top 5 by Suggested Priority Rank table.

## 14a. The Job Posting Quick Links Tab (and Its Limits)

If Add a Job Posting Quick Links tab? is Yes, the tracker gets a sheet with three HYPERLINK() formulas per company — LinkedIn Jobs, Indeed, and Google Jobs searches, pre-filled with company name and one job title.

*Say this plainly: this tab does not contain jobs, it contains links. Clicking one just opens a live search — exactly as if you'd typed it yourself.*

This is the cheap, safe option — it costs no extra research, pure string templating from data already generated in the main tracker.

## 15. The Job Post Finder Tab

If Add a Job Post Finder tab? is Yes, the tracker gets a minimal sheet: Company Name and the full Suggested Job Title Keywords cell (all variants, not reduced to one), nothing else — no formulas, no hyperlinks.

Different moment than Quick Links: that tab gives pre-built links to three platforms using one title; this tab gives the raw ingredients — company plus all keyword variants — to paste into whatever job board or search tool you actually want to use.

## 16. The Outreach Contacts Tab

If Add an Outreach Contacts tab? is Yes, the tracker gets a four-column sheet — Company, Key Contacts / Priority Titles, Warm Introduction Path, Category, in that exact order — copied straight from the main tracker. These four columns aren't adjacent on the main sheet, so this tab exists purely to put them side by side for a clean copy-paste into the companion Outreach Message Builder tool's bulk-paste box.

## 17. The Industry Events & Forums Tab (and How Category Drives It)

If Yes, adds a tab of real, upcoming conferences and trade shows — one row per event, not per company. The Relevant To column reuses your main sheet's Category values directly, so it stays connected to however your companies are already grouped.

Same honesty standard as everywhere else: only real, currently findable events with a real URL. Thin coverage is reported directly rather than invented.

## 18. The Company Activity & Events Tab

Off by default. One row per company instead of per event — recent LinkedIn activity, podcast/webcast appearances, upcoming events that company is attending or speaking at.

A meaningfully harder research task than Industry Events. Claude checks each company from a few different angles (LinkedIn page directly, podcast/webinar search, conference/sponsor search) before concluding there's nothing. Expect real unevenness — many rows will legitimately read "No recent public activity found" or, for a large batch, "not individually checked this pass," which is the honest result, not a sign something's broken.

## 19. Key Contacts and 10-K Filings

For publicly traded companies specifically, a second data point is layered on top of the practice-level Key Contact: a check of the company's most recent 10-K for a named individual responsible for cybersecurity governance (SEC Regulation S-K Item 106 / Item 1C). When found, added as a clearly labeled second line: "(per FY20XX 10-K)."

- Only applies to companies that file a 10-K at all — most pure-play vendors are privately held.
- It's the enterprise-wide security executive, not necessarily an OT-specific one.
- Not every public company names someone — when that happens, the tracker says so directly.
- It's only as current as the filing.

## 20. Compensation Benchmark

If the named 10-K individual also appears in the company's proxy statement (DEF 14A) as a Named Executive Officer, their disclosed total compensation is reported alongside them.

*This will genuinely apply to a minority of companies — proxy statements only disclose compensation for the top handful of executives, and a security-specific role is rarely among them.*

## 21. Section 3 — LinkedIn Contact Enrichment

A separate, self-contained card at the bottom of the page. This is a fully independent feature — it doesn't touch or require the Section 2 tracker, and generates its own standalone prompt with its own Copy/Download buttons.

**What it does:** cross-references a LinkedIn contacts export against a list of target companies, to surface which of your existing connections work (or worked) at each one.

**How to use it**

- Paste your target companies into the box, one per line — the Company column from a Section 1 or Section 2 tracker works directly.
- Keep the list to 25 companies or fewer — the tool warns inline if you go over. The expensive part here is the number of contacts to fuzzy-match against, not the company count, so a long list slows matching and can hurt accuracy.
- Copy or download the generated prompt.
- Start a new Claude conversation, paste the prompt in, and attach your LinkedIn contacts CSV export directly to that same message. This tool never uploads, parses, or reads the CSV itself.

**What you get back:** for each target company, any matching contacts — name, title, LinkedIn URL, current/former status, and a Match Confidence rating. Companies with no match are listed as "No match found" rather than dropped.

## 22. A Faster Way to Fill This Out (Reverse Note)

If you'd rather not use the web form at all, there's a companion plain-text template — Target_Company_Research_Prompt_Template (.md) — with the same fields laid out as fill-in-the-blank text you can paste directly into a Claude chat. Use whichever format is more convenient in the moment; both produce the same result. (Note: this template covers Section 2 only — Section 1 and Section 3 don't have a plain-text equivalent yet.)
