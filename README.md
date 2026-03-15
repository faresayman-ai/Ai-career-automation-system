## 🎯 AI Career Path Automation System — Skill Journey

An n8n workflow that generates personalized, AI-powered learning roadmaps using Gemini 2.5 Flash Lite and delivers them as professionally styled HTML emails.

---

## 📌 Overview

Skill Journey is an automated pipeline designed to transform user goals into structured educational plans. Unlike static templates, this system polls a Google Sheet for new responses, filters out already processed entries, and uses the Gemini 2.5 Flash Lite model to draft a custom roadmap. A dedicated JavaScript layer ensures the AI's output is sanitized and valid HTML before it is emailed to the user.

**Scalable, polished, and data-driven.**

---

## ✨ Features

- **🔄 Polling Trigger** — Automatically checks Google Sheets every minute for new "Skill Journey" form responses.
- **🧠 Advanced AI Reasoning** — Uses gemini-2.5-flash-lite via OpenRouter to generate deep, age-appropriate, and goal-specific roadmaps.
- **🧹 JS Output Sanitization** — A dedicated Code node strips Markdown backticks (```html) from AI responses to ensure 100% valid HTML delivery.
- **🎨 Dynamic HTML Styling** — The AI is programmed to inject specific hex-code palettes (#1a3a2e, #b87c1e, etc.) directly into the email body.
- **➰ Batch Processing** — Uses "Loop Over Items" to handle multiple new sign-ups in a single execution without timeouts.
- **✅ Status Synchronization** — Updates the Google Sheet "Status" column to Done only after the email has been successfully sent.
---

## 🔧 Tech Stack

| Tool | Role |
|------|------|
| [n8n](https://n8n.io) | Workflow automation engine |
| Gemini 2.5 Flash Lite | Roadmap generation |
| OpenRouter | LLM API Gateway |
| Google Sheets | Database & Trigger source |
| JavaScript | Data cleaning & String manipulation |

### Required Credentials
- OpenRouter API (for Gemini 2.5 access)
- Google Sheets OAuth2
- Google Sheets Trigger OAuth2
- Gmail OAuth2

---

## 🗂️ Workflow Architecture

```
Google Sheets Trigger (Every Minute)
  └── Filter (If 'Status' is empty)
        └── Loop Over Items
              └── AI Agent (Gemini 2.5 Flash Lite)
                    └── Code Node (Regex HTML Cleanup)
                          └── Gmail (Send Styled Roadmap)
                                └── Update Google Sheet (Set Status to "Done")
```

---

## 📬 Sample Output

The AI generates a sophisticated HTML document with:
- **Personalized Greeting** : "Welcome [User Name]"
- **Color-Coded Phases** : Structured <section> tags with specific brand colors.
- **Deep Content** : Integration of specific topics, practical projects, and resources.
- **Visual Hierarchy** : Styled borders and backgrounds (#e8f5ec) for readability.
---

## 🚀 How to Use

### Prerequisites
- [n8n](https://n8n.io) (self-hosted or cloud)
- OpenRouter API Key
- A Google Sheet with columns: Timestamp, Your Name, Your Gmail, What are the skills you want to learn?, What period of time..., Why you want to learn it ?, and Status.

### Setup

1. **Import the workflow**
   - In n8n, go to **Workflows → Import**
   - Upload `Skill_Journey.json`

2. **Configure credentials**
   - Add your **OpenRouter Chat Model** key
   - Add your **Google Sheets OAuth2** credentials
   - Add your **Gmail OAuth2** credentials

3. **Map the Sheet**
   - Ensure the Document ID in the Trigger and Update nodes matches your specific Google Sheet ID.

4. **Activate and test**
   - Flip the workflow to Active. It will now check your sheet every 60 seconds.

---

## 📁 Files

| File | Description |
|------|-------------|
| `Skill_Journey.json` | n8n workflow export (import this into n8n) |

---
## 🔗 Live Demo
 
Try the live deployment here:
 
**[(https://faresayman-ai.github.io/Ai-career-automation-system/)**
 
> Submit a skill goal and receive a personalized roadmap directly in your inbox. Processes requests in under 15 seconds.
---

*Built with n8n + Gemini-2.5 Flash Lite. Processes career planning requests in under 15 seconds.*
