# Multi-Tool AI Agent (n8n + OpenAI)

A Telegram assistant for a creative studio that **decides on its own which tool to use**: business data, a live API, or math.


## How it works
1. **Telegram Trigger**: the user sends a question.
2. **AI Agent** (OpenAI `gpt-4o-mini`) reads it and picks the right tool(s):
   - **Leads sheet** (Google Sheets): looks up incoming leads and their AI scores.
   - **Exchange Rates** (HTTP Request tool): live rates from `open.er-api.com`.
   - **Calculator**: exact math, no AI guessing.
3. **Telegram** sends the answer back to the same chat.

**Examples:**
- "What's the USD to VND rate and what is 15% of 5000?" → calls Exchange Rates + Calculator → "About 25,847 VND per 1 USD. 15% of 5000 is 750."
- "How many leads do I have and which has the highest score?" → calls Leads sheet → "You have one lead, the highest score is 8."

## Stack
n8n · OpenAI · LangChain AI Agent · Google Sheets · REST API · Telegram Bot API

## What I learned
- Tool-calling agents: writing tool descriptions so the model picks the right tool.
- Connecting each tool directly to the agent's Tool port (not chaining tools).
- Combining several tools in one answer.

## Setup
Import `workflow.json`, replace `YOUR_GOOGLE_SHEET_ID` with your own sheet, and add your OpenAI, Google Sheets and Telegram credentials (none are included).
