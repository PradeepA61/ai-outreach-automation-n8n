AI-Powered Lead Outreach Workflow using n8n
Overview

This repository contains an n8n workflow that automates lead capture, filtering, AI-generated personalized outreach messages, and logging results in Google Sheets.
The workflow captures incoming leads via a webhook, filters them based on criteria (bio containing “AI” and followers > 500), generates friendly AI messages, and stores accepted and rejected leads in separate Google Sheets.

Workflow Nodes
Webhook – Receives incoming lead data (username, bio, followers).
Edit Fields – Maps the incoming payload into structured fields.
If Node – Filters leads based on:
Followers greater than 500
Bio containing the keyword “AI”
AI Agent (LangChain) – Generates a personalized, friendly outreach message using an AI model.
Code Node – Parses AI output and formats it into JSON.
Edit Fields (Accepted / Rejected) – Adds status, reason, and timestamp for tracking.
Google Sheets Append Rows – Stores accepted and rejected leads in separate sheets.
Respond to Webhook – Sends back a success or rejection response.
Setup Instructions
Clone the repository:
git clone https://github.com/<your-username>/ai-outreach-automation-n8n.git
Import workflow in n8n:
Go to n8n → Workflows → Import → Select workflow.json.
Configure credentials:
Google Sheets OAuth2 – connect to the Google Sheets for storing leads.
AI Model API (Groq / LangChain) – add your API key securely.
Webhook Testing:
Use dummy leads to test the workflow (do not use real accounts):
{
  "username": "TestUser123",
  "bio": "AI enthusiast and developer",
  "followers": 600
}
Tool Choices
n8n – Visual automation platform for building workflows.
LangChain AI Agent – Generates personalized outreach messages.
Google Sheets – Simple database to store accepted and rejected leads.
Sample Output
Username	Bio	Followers	AI Message	Status	Reason	Time
TestUser123	AI enthusiast and dev	600	“Hi TestUser123, loved your AI bio!”	Accepted	Valid lead	2026-03-28 12:00
Improvements with More Time / Budget
Add automated scheduling for outreach messages.
Support multi-platform lead collection (Instagram, LinkedIn, Twitter).
Implement richer AI personalization based on bio keywords.
Create an analytics dashboard for tracking outreach performance.
Enhance error handling and logging for failed runs.
