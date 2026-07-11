# Target Company Research Prompt Builder

A single self-contained HTML tool that turns a few form fields into a ready-to-send Claude prompt for researching target companies (job search targets, sales prospects, partnership candidates, or M&A targets) and building a formatted, color-coded Excel tracker — complete with a computed priority ranking, an optional "your background" field for personalized outreach guidance, and an optional one-click job-posting search-links tab.

**[Open the live tool](https://tjackson8817.github.io/Target-Company-Prompt-Builder/prompt_builder.html)**

No install, no account, nothing sent anywhere — it's a static form that assembles text entirely in your browser.

## Files in this repo

| File | What it is |
|---|---|
| `prompt_builder.html` | The interactive tool. Open it directly in any browser, or use the GitHub Pages link above. |
| `Prompt_Builder_User_Guide.md` | Full usage guide — every field explained, plus how to read the formatted output tracker. |
| `Prompt_Builder_User_Guide.docx` | Same guide, as a Word document. |
| `Target_Company_Research_Prompt_Template.md` | A plain-text, fill-in-the-blank version of the same prompt, for anyone who'd rather skip the form. |
| `NOTES.md` | Compatibility notes — built for Claude, but the generated prompt is plain text and portable to other AI tools. |

## Quick start

1. Open `prompt_builder.html` (via GitHub Pages, or download and double-click it).
2. Fill in whatever starting-point info you have — a company name, an industry description, a NAICS code, or any combination.
3. Set your scope and purpose.
4. Copy the generated prompt from the right-hand panel.
5. Paste it into a new chat with Claude and send it.
6. Claude researches the companies and returns a formatted, color-coded `.xlsx` tracker.

See `Prompt_Builder_User_Guide.md` for the full walkthrough, including what each output column means and how the color-coding and priority scoring work.

## Notes

- This repo can be public or private — GitHub Pages on the free tier requires a public repo (or a paid plan for private-repo Pages).
- If you use this to research your own target list, keep that output file (the `.xlsx` tracker) local — it's not meant to be committed here.
