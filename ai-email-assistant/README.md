# AI Email Assistant (n8n)

An AI-powered email assistant built using n8n that automatically classifies
incoming emails and organizes them using Gmail labels, with optional AI-based
summaries for job-related messages.

This workflow focuses on high-volume email triage, categorization, and
lightweight AI augmentation rather than full agent-based responses.

---

## Overview

The AI Email Assistant listens for incoming Gmail messages and uses an LLM-based
text classifier to categorize emails into predefined groups such as jobs,
personal messages, newsletters, promotions, and security notifications.

Based on the classification, the workflow applies the appropriate Gmail label
and optionally generates concise summaries for job-related emails.

---

## Workflow Logic

1. **Gmail Trigger**
   - Detects new incoming emails

2. **Text Classification (LLM)**
   - Classifies emails into predefined categories:
     - Jobs
     - Personal
     - Newsletters
     - Promotions
     - Security notifications
     - Subscription updates
     - Miscellaneous

3. **Conditional Labeling**
   - Applies Gmail labels automatically based on classification
   - Keeps inbox organized without manual intervention

4. **Job Email Summarization**
   - For job-related emails, uses an LLM to extract:
     - Company
     - Role
     - Location
     - Employment type
     - Deadlines (if present)
   - Sends summaries via Telegram for quick review

---

## Key Concepts Demonstrated

- AI-based text classification
- Event-driven automation
- Email triage and labeling
- Conditional routing
- API integrations (Gmail, OpenAI, Telegram)
- Structured prompts for information extraction

---

## Tech Stack

- **Automation:** n8n
- **LLMs:** OpenAI
- **Email:** Gmail API
- **Notifications:** Telegram
- **Data Format:** JSON

---

## Credentials & Security Notes

- All credentials (OpenAI, Gmail, Telegram) are managed securely in n8n and
  are **not included** in exported workflow files.
- Shared `.json` files contain only workflow logic and configuration.
- This is the standard approach for versioning and sharing n8n workflows.

---

## Notes

- Workflow is shared as an exported `.json` file.
- Designed as a personal automation and learning project.
- Not intended as a production-ready drop-in solution.
