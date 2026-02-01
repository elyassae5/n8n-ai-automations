# AI Daily Pulse (n8n)

An AI-powered daily briefing agent built with n8n that gathers the latest and most interesting AI-related news, adds a fun science fact from Wikipedia, formats everything into a clean email newsletter, sends it via Gmail, and logs results into Google Sheets.

---

## What this agent does

- Reviews previous daily briefings from Google Sheets to avoid repetition
- Searches the web for **recent AI news** using SerpAPI
- Selects the **top 3 most interesting AI stories**
- Pulls **one fun or fascinating science-related fact** from Wikipedia
- Generates a concise, readable AI newsletter
- Formats the output into modern, email-safe HTML
- Sends the briefing via Gmail
- Logs the news and fun fact into Google Sheets

---

## How it works (high level)

1. Schedule trigger starts the workflow
2. Agent reviews previous entries in Google Sheets
3. AI Agent is forced to use:
   - SerpAPI for current AI news
   - Wikipedia for a science fun fact
4. Agent generates the daily briefing
5. Markdown is converted to HTML
6. HTML is beautified for email
7. Email is sent via Gmail
8. News + fun fact are appended to Google Sheets

---

## Google Sheet schema

| Column    | Description                              |
|-----------|------------------------------------------|
| Date      | Execution timestamp                      |
| News      | AI news summary (3 items)                |
| Fun Fact  | Science-related fun fact from Wikipedia  |

---

## Safety rules enforced

- No repeated news or fun facts
- Read-before-write enforced via prompt design
- External tools required (no hallucinated news)
- Credentials are never stored in the workflow
- No destructive actions

---

## Tech stack

- n8n (self-hosted)
- OpenAI (GPT-4.1 / GPT-4.1-mini)
- SerpAPI
- Wikipedia API
- Gmail (OAuth2)
- Google Sheets (OAuth2)
- LangChain AI Agent node

---

## Notes

- Credentials are **not included** in this repository
- OAuth connections must be configured after importing the workflow
- Tools (SerpAPI, Wikipedia) are explicitly forced via system prompts
- Designed for scheduled, unattended execution

---

## License

MIT License
