[README.md](https://github.com/user-attachments/files/29889587/README.md)
# Target Company Research Prompt Builder

A single self-contained HTML tool that turns a few fields — a company name, an industry, a NAICS code, or all three — into a complete, ready-to-send research prompt for Claude. Paste the generated prompt into a new chat and Claude researches the companies and hands back a formatted, downloadable Excel tracker.

No install, no account, no server. It's one HTML file that runs entirely in your browser.

**[Open the live tool →](https://tjackson8817.github.io/Target-Company-Prompt-Builder/prompt_builder.html)**
*(replace with your actual GitHub Pages URL once it's live — see "Deploying" below)*

---

## What it does

- Fill in a company you know, an industry in plain language, and/or a NAICS code — one is enough, and you can combine them
- Choose **Discovery Scope**: have Claude find new candidate companies via NAICS discovery, or just research the exact companies you listed
- Optionally exclude companies you've already contacted, so they don't get resurfaced
- Optionally turn on **M&A research columns** — ownership type, recent deal activity, and a buyer-vs-target read on each company
- The right-hand panel builds the actual prompt live as you type — copy it or download it as a `.txt` file
- Save your common searches as named templates (e.g. "OT Vendors," "Big 4 Consulting") so you're not retyping them every time

## How to use it

1. Open the tool (the live link above, or by opening `prompt_builder.html` directly in a browser).
2. Fill in whichever fields apply to your search.
3. Copy the generated prompt from the right panel.
4. Paste it into a new Claude chat and send it.
5. Claude researches the companies and delivers a formatted `.xlsx` you can download.

## Running it locally

No setup required:

```bash
git clone https://github.com/tjackson8817/Target-Company-Prompt-Builder.git
cd YOUR-REPO-NAME
open prompt_builder.html   # macOS
# or just double-click the file in Finder/Explorer
```

Or skip git entirely — download `prompt_builder.html` from this repo and double-click it.

## Deploying this yourself (GitHub Pages)

If you've forked or cloned this repo and want your own live link:

1. In your repo, go to **Settings → Pages**.
2. Under "Build and deployment," set **Source** to **Deploy from a branch**.
3. Choose branch `main`, folder `/ (root)`, click **Save**.
   - If `main` doesn't appear in the dropdown, you need at least one commit on the repo first — upload `prompt_builder.html` via **Add file → Upload files** and commit, then return to this step.
4. After a minute or two, GitHub gives you a live URL in the form:
   `https://tjackson8817.github.io/Target-Company-Prompt-Builder/prompt_builder.html`
5. Update the link at the top of this README with your real URL.

## A note on privacy

This tool has no backend and no accounts. Everything you type lives only in your own browser tab while it's open — nothing is sent anywhere, and nothing is visible to anyone else using the tool, even if they're using the exact same file at the same time. If you want to keep your saved templates between sessions, use the **Export (.json)** / **Import (.json)** buttons inside the tool to save/reload them as a file — they don't persist automatically.

## Files in this repo

| File | What it is |
|---|---|
| `prompt_builder.html` | The tool itself — open this in a browser |
| `README.md` | This file |
