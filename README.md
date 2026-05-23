# 🚀 Developer Launchpad: Automated n8n Marketing Workflow

<p align="center">
  <img src="https://img.shields.io/badge/n8n-compatible-orange.svg?style=for-the-badge&logo=n8n" alt="n8n Compatible" />
  <img src="https://img.shields.io/github/stars/Eccys/developer-launchpad-n8n?style=for-the-badge&color=yellow" alt="Stars" />
  <img src="https://img.shields.io/github/license/Eccys/developer-launchpad-n8n?style=for-the-badge&color=blue" alt="License" />
</p>

<p align="center">
  <b>A production-ready n8n workflow template to cross-post your new tools, libraries, or side-projects to Reddit, Twitter/X, Dev.to, and Discord with a single API call.</b>
</p>

---

## 🛠️ How It Works

This workflow listens for a Webhook trigger containing your project details (`title`, `url`, `description`) and executes the following in parallel:
1. **Reddit Node:** Submits a link post to your target subreddit (e.g., `/r/github`, `/r/opensource`).
2. **Twitter Node:** Posts an announcement tweet complete with hashtags and links.
3. **Dev.to API:** Creates a structured draft post on Dev.to (`showdev` category) with markdown placeholders.
4. **Discord Webhook:** Sends a notification to your server with a **pre-filled, one-click link to submit to Hacker News** (bypassing Hacker News' read-only API limitation).

---

## 🚀 Setup and Installation

### 1. Import to n8n
1. Download the [marketing_workflow.json](marketing_workflow.json) file.
2. In your n8n dashboard, click **Workflows > Import from File** and select the JSON.
3. The workflow editor will automatically load all the trigger, formatting, and social nodes.

### 2. Configure Credentials
Inside n8n, click on each node to authorize your accounts:
* **Reddit:** Add a Reddit OAuth2 credential.
* **Twitter:** Add a Twitter API v2 / OAuth2 credential.
* **Dev.to (HTTP Request):** Replace `YOUR_DEVTO_API_KEY_HERE` in the headers with your Dev.to API Key (obtainable from settings -> developer on Dev.to).
* **Discord (Webhook):** Add your Discord webhook URL to receive alerts.

---

## 📡 How to Trigger the Launch

You can trigger the launch sequence from your terminal, CI/CD pipeline, or deployment script using a simple `curl` request to your n8n webhook URL:

```bash
curl -X POST https://YOUR_N8N_INSTANCE_URL/webhook/developer-launch \
  -H "Content-Type: application/json" \
  -d '{
    "title": "GitHub Profile Enhancer - Premium README Generator",
    "url": "https://github.com/Eccys/github-profile-enhancer",
    "description": "An interactive CLI tool to generate stunning profile layouts, metrics widgets, and sponsors buttons."
  }'
```

---

## 📄 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
