# Mail-Inbox-Triage

An LLM-powered email triage and security analysis application built using **Python, LangChain, and Google Gemini**.

The system analyzes emails based on their **priority, required action, sender legitimacy, deadlines, external links, attachments, and phishing risk**. It is designed to demonstrate how LLMs can be used to build practical AI applications beyond simple chatbots.

The current implementation uses a **LangChain pipeline** with Google Gemini. A planned extension is to use **LangGraph** for conditional routing, security verification, human review, and final inbox ranking.

---

## Overview

Modern inboxes contain a mixture of important deadlines, interviews, bills, notifications, newsletters, advertisements, and potentially malicious emails.

Simply sorting emails based on keywords such as `URGENT` or `IMPORTANT` is not sufficient.

For example:

- A placement registration email may be **HIGH priority and LOW phishing risk**.
- A fake account suspension email may be **HIGH priority but HIGH phishing risk**.

Therefore, this project treats **priority and security risk as separate dimensions**.

```text
                         Email
                           |
              +------------+------------+
              |                         |
              v                         v
        Priority Analysis        Security Analysis
              |                         |
        HIGH/MEDIUM/LOW          LOW/MEDIUM/HIGH
              |                         |
              +------------+------------+
                           |
                           v
                    Action Analysis
                           |
                           v
                    Email Ranking
```

# Objectives

The main objectives of the project are:

  1. Classify emails into HIGH, MEDIUM, and LOW priority.
  2. Determine whether an email requires user action.
  3. Identify deadlines and time-sensitive actions.
  4. Analyze whether the sender appears legitimate.
  5. Detect potential phishing and scam indicators.
  6. Identify suspicious links and domain impersonation.
  7. Distinguish between an action requested by an email and the action that should actually be recommended to the user.
  8. Rank emails based on urgency and required action.
  9. Provide a foundation for extending the application into a LangGraph-based workflow.


# Features
  1. Email Priority Classification
  2. Sender Validity Analysis
  3. Phishing Risk Detection
  4. Action Analysis
  5. Security aware Action recommendation

# Architecture:
Current architecture uses LangChain chain ->

```text
              Email Dataset
                    |
                    v
             PromptTemplate
                    |
                    v
        ChatGoogleGenerativeAI
                    |
                    v
             Google Gemini
                    |
                    v
             Email Analysis
                    |
          +---------+---------+
          |         |         |
          v         v         v
       Priority  Security   Action
       Analysis  Analysis   Analysis
          |         |         |
          +---------+---------+
                    |
                    v
             Structured Output
```

# Technology Stack:

| Technology               | Purpose                      |
| ------------------------ | ---------------------------- |
| Python                   | Core implementation          |
| LangChain                | LLM application pipeline     |
| Google Gemini            | Large Language Model         |
