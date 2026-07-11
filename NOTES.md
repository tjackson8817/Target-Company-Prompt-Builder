# About This Tool & Cross-Platform Compatibility

## Built for Claude

The Target Company Prompt Builder was designed, built, and tested for use with **Claude** (Anthropic). The prompt it generates is written to match how Claude interprets instructions, structures research, and formats output — including building a formatted `.xlsx` tracker directly in the conversation.

## Using the output prompt with other AI tools

The `.txt` prompt this tool generates is plain text, so it isn't locked to Claude — you're free to paste it into other generative AI apps (ChatGPT, Gemini, Copilot, etc.). A few things to expect if you do:

- **Some apps will run it as-is** and return comparable results.
- **Some may need minor edits** — for example, a tool without built-in spreadsheet-creation ability might return the same research as a formatted table or CSV text instead of a downloadable `.xlsx` file, or may need to be told explicitly how to output the data.
- **Some may offer their own suggestions** for how to restructure or run the prompt based on that platform's particular strengths or limitations.

None of this means the prompt is broken elsewhere — it just means results, formatting, and follow-up behavior may vary by platform. If you get inconsistent results on a non-Claude tool, try simplifying the request (fewer companies, fewer columns) or asking that tool directly how it would prefer the prompt restructured.

## The overall goal

However you run it, the goal of this tool stays the same: make it easy to enter your key target-company attributes — a company you know, an industry, a NAICS code, your purpose — and generate a clear, complete prompt that's easy for *you* to read, edit, and adapt before you run it anywhere.
