# AI Resume Screener (n8n + Google Gemini)

An automated resume screening workflow built with n8n that reads resumes sent via email, compares them against a job description, and generates a structured evaluation — strengths, weaknesses, risk/reward analysis, and an overall fit score — logged automatically to Google Sheets.

## Overview

This workflow demonstrates an end-to-end AI recruitment automation: handling file attachments, converting document formats, extracting text, running LLM-based reasoning against a job description, and structuring the output for easy review.

## How It Works

1. **Gmail Trigger** — listens for incoming emails with resume attachments (Word, PDF, or text files)
2. **Google Drive Upload** — saves the resume attachment to a designated Drive folder
3. **Format Routing** — a Switch node routes the file based on type (Word/PDF/Text)
4. **Document Conversion & Text Extraction** — Word files are converted to a readable format and extracted to plain text
5. **AI Agent (Gemini)** — an LLM agent compares the resume text against a stored job description and evaluates the match, following a structured output schema
6. **Information Extraction** — pulls the candidate's first name, last name, and email from the resume text
7. **Google Sheets Logging** — all results are appended as a new row: date, resume link, candidate info, strengths, weaknesses, risk factor, reward factor, overall fit (0–10), and justification

## Output Fields

| Field | Description |
|---|---|
| Strengths | Specific qualifications matching the job description |
| Weaknesses | Gaps or mismatches relative to the role |
| Risk Factor | Low/Medium/High, with an evidence-based explanation |
| Reward Factor | Low/Medium/High, with potential value/fit explanation |
| Overall Fit | A 0–10 score |
| Justification | Reasoning behind the score, referencing resume content |

## Tech Stack

- **n8n** — workflow automation and orchestration
- **Google Gemini API** (`gemini-3.5-flash-lite`) — resume analysis and structured reasoning
- **Gmail API** — trigger for incoming resumes
- **Google Drive API** — file storage and format conversion
- **Google Sheets API** — results logging

## Setup

To use this workflow yourself:

1. Import the `.json` file into your own n8n instance
2. Connect your own Gmail, Google Drive, and Google Sheets accounts (OAuth2)
3. Generate a free Google Gemini API key at [Google AI Studio](https://aistudio.google.com/apikey) and connect it as a credential
4. Replace the job description document reference and the Google Sheet reference with your own
5. Adjust the evaluation prompt/schema as needed for your role or use case

No credentials or API keys are included in this repository — all connections must be configured with your own accounts.

## Notes

- This is a portfolio/demo project. The workflow is kept **inactive** in n8n and was only run manually for testing.

## Demo

[Watch the demo video](https://youtu.be/XFQWmCpasDk?si=tNsjDbDBT8-dnFIA)
