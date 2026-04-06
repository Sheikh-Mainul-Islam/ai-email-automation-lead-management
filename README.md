# AI Email Automation & Lead Management System

![n8n Workflow Configuration](workflow-screenshot.png)
*(Note: Upload your workflow image to GitHub and make sure it is named workflow-screenshot.png)*

## 📨 Overview
Welcome to the **AI Email Automation & Lead Management System**. This project is a fully automated, intelligent email auto-responder and lightweight CRM built entirely within [n8n](https://n8n.io/). 

Instead of relying on rigid, robotic email templates, this system uses advanced LLMs via OpenRouter and a custom JavaScript matching engine to read incoming business emails, categorize leads, answer FAQs dynamically, and log everything seamlessly into Google Sheets. 

## ✨ Key Features

* **Smart Inbox Monitoring:** Automatically triggers on new Gmail messages while proactively filtering out newsletters, "no-reply" addresses, and system notifications.
* **Intelligent FAQ Match Engine:** A custom-built routing system that cross-references incoming emails against a structured Google Sheets Knowledge Base.
* **Human-Like AI Responses:** Powered by `gpt-oss-120b` (via OpenRouter), the system generates polite, natural, and highly contextual replies. It avoids sounding formal, salesy, or robotic.
* **Automated Lead Tracking (Google Sheets CRM):** * Checks if an email is a **New** or **Existing** lead.
  * Automatically logs lead details (Name, Email, Message, AI Response, Status, and Timestamps).
* **Smart Status Escalation:** * Simple queries are answered and marked as **ACTIVE**.
  * Complex queries that bypass the FAQ are answered generally and marked to **ESCALATE** for human review.
* **Bulletproof Error Handling:** Any workflow failure is automatically caught, logged into an `ERROR_LOG` Google Sheet, and an immediate alert email is sent to the administrator.

## 🛠️ System Architecture (How it Works)

1. **Trigger & Clean:** A new email arrives. The system parses the sender's details and strips out any spam/marketing bots.
2. **Database Check:** The system queries the `LEADS` Google Sheet to see if this user has emailed before.
3. **Routing & Logic:**
   * **Path A (FAQ Match):** The system checks the `FAQ_KNOWLEDGE` sheet. If a strong keyword match is found, the AI formats the approved answer and replies instantly.
   * **Path B (Custom Reply):** If the question isn't in the FAQ, the AI reads the email and crafts a professional, human-sounding response asking for clarification or providing general assistance.
4. **Update & Alert:** The lead's row in Google Sheets is updated with the latest AI response and status, keeping your pipeline perfectly organized.

## ⚙️ Prerequisites & Setup

To run this workflow yourself, you will need:
* An active **n8n** instance (Cloud or Self-Hosted).
* **Google Cloud Console Credentials:** OAuth2 setup for both Gmail and Google Sheets APIs.
* **OpenRouter API Key:** For accessing the LLM models.
* A **Google Sheet** formatted with three specific tabs:
  * `LEADS`
  * `FAQ_KNOWLEDGE`
  * `ERROR_LOG`

*(Remember to update the API Keys and Google Sheet IDs in the JSON file before importing into your own environment!)*

## 👨‍💻 Author

**Sheikh Mainul Islam**
*AI & Automation Consultant*

I specialize in building intelligent automation systems that streamline business workflows, reduce manual effort, and improve response efficiency using AI.

💼 **Open to freelance & collaboration opportunities**
* 🌐 **GitHub:** [Sheikh-Mainul-Islam](https://github.com/Sheikh-Mainul-Islam)
* 📧 **Email:** sheiikhmainul1@gmail.com

Feel free to fork this repository, customize the workflow, and use it to automate your own email operations!
