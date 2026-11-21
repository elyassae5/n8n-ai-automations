# n8n AI automations

Four AI agents and automations built in [n8n](https://n8n.io), each exported as a workflow JSON with its own README. They ran on a self-hosted n8n instance. Credentials are not part of the exports.

| Folder | What it does | Main pieces |
|---|---|---|
| [`ai-daily-briefing`](ai-daily-briefing/) | Daily AI news briefing: an agent finds the top 3 AI stories and a science fact, formats an HTML email, sends it and logs it to Google Sheets so it does not repeat itself | Schedule trigger, AI agent, SerpAPI, Wikipedia, Gmail, Google Sheets |
| [`ai-email-agent`](ai-email-agent/) | Support email agent: classifies incoming mail, looks up the answer in a knowledge base and drafts a reply | Gmail trigger, AI agent, OpenAI embeddings, Pinecone vector store (RAG), Telegram |
| [`ai-email-assistant`](ai-email-assistant/) | Inbox triage: an LLM classifier sorts mail into categories, applies Gmail labels and summarizes job emails | Gmail trigger, text classifier, Gmail labels, Telegram |
| [`subscription-tracker-agent`](subscription-tracker-agent/) | Chat agent that tracks subscriptions in Google Sheets from plain messages, reads before it writes and asks before it changes anything | Chat trigger, AI agent with memory, Google Sheets tools |

All four use OpenAI chat models through n8n's LangChain nodes.

## Run one

1. Start n8n, for example with Docker: `docker run -it --rm -p 5678:5678 n8nio/n8n`, then open http://localhost:5678.
2. Create a workflow, open the menu and choose **Import from File**, then pick the JSON from the folder.
3. Add your own credentials for the nodes that need them (OpenAI, Gmail, Google Sheets, and per workflow SerpAPI, Pinecone or Telegram).
4. Point the Google Sheets and Pinecone nodes at your own sheet or index, then activate the workflow.

The README in each folder has the details: the flow step by step, the sheet layout and the rules the agent follows.
