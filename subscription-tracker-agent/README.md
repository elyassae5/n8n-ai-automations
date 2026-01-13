# AI Subscription Tracker (n8n)

An AI-powered agent built with n8n that tracks user subscriptions and recurring expenses in Google Sheets while preventing duplicate entries and unsafe writes.

## What this agent does

- Accepts natural language messages (e.g. “Cancel Netflix”, “Spotify is now $12”)
- Extracts structured subscription data
- Confirms intent before making changes
- Checks for existing entries before writing
- Updates or appends rows safely in Google Sheets

## Why this exists

This workflow demonstrates:
- Safe AI agent design
- Tool-based reasoning (read → decide → write)
- Confirmation-driven mutations
- Practical use of LLMs beyond chat

## Architecture

1. Chat trigger receives user message  
2. AI Agent interprets intent and extracts fields  
3. Read tool checks Google Sheet for existing subscription  
4. Agent confirms understanding with the user  
5. Write tool updates or appends data  

## Google Sheet schema

| Column       | Description                     |
|-------------|---------------------------------|
| Expense     | Subscription name (primary key) |
| Charge Date | YYYY-MM-DD                      |
| Cadence     | Monthly / Yearly / etc.         |
| Cost        | Numeric cost                    |
| Status      | Active / Canceled / Paused      |

## Safety rules enforced

- No writes without user confirmation
- No duplicate subscriptions
- No destructive actions
- Read-before-write enforced via prompt design

## Tech stack

- n8n (self-hosted)
- OpenAI (GPT-4.1-mini)
- Google Sheets API (OAuth2)
- LangChain Agent node

## Notes

Credentials are not included in this repository.
