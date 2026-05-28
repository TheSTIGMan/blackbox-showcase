# Blackbox — SOC Agent Prototype

Blackbox is a Security Operations Center (SOC) simulation dashboard. You click one button to generate a realistic cybersecurity incident, and a second button to run a two-stage AI pipeline that classifies the incident and then critiques its own classification — all using a locally hosted AI model. No data ever leaves your machine.

Think of it as a training tool: it shows how SOC analysts triage incidents using a real framework (NIST SP 800-61), with an AI acting as both the first analyst and the quality reviewer.

---

## Features

- **Incident Generator** — creates realistic mock cybersecurity incidents across 14 different attack scenarios (ransomware, DDoS, insider threat, phishing, SQL injection, and more)
- **SOC Classifier** — scores each incident across three NIST SP 800-61 dimensions: Functional Impact, Information Impact, and Recoverability, then assigns an overall severity (Low / Medium / High / Critical)
- **Validation Agent** — acts as a critic: independently checks the classifier's work and either confirms it or flags it with a specific explanation of what was wrong
- **Live progress streaming** — the dashboard shows "Classifying incident 2 of 5… Validating incident 2 of 5…" in real time as the pipeline runs
- **Google Sheets log** — every incident and its full classification is written to a shared Google Sheet for review and record-keeping
- **Delete incidents** — remove rows from the dashboard and the sheet with one click
- **Expandable rows** — click any incident to see the full description, NIST scores, reasoning, and validation notes
- **Offline detection** — buttons are disabled and a banner appears if LM Studio is not running

---

## Tech Stack

![Python](https://img.shields.io/badge/Python-3.11+-3776AB?style=flat&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-0.115+-009688?style=flat&logo=fastapi&logoColor=white)
![React](https://img.shields.io/badge/React-18-61DAFB?style=flat&logo=react&logoColor=black)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3-06B6D4?style=flat&logo=tailwindcss&logoColor=white)
![Google Sheets](https://img.shields.io/badge/Google_Sheets-API-34A853?style=flat&logo=googlesheets&logoColor=white)
![LM Studio](https://img.shields.io/badge/LM_Studio-Local_LLM-7C3AED?style=flat)

---

## How It Works

```
Generate Incident  →  AI Agent 1  →  new row in Google Sheet (columns 1–6)

Run SOC Agent      →  for each unclassified row:
                        AI Agent 2 (classify)  →  AI Agent 3 (validate)  →  write columns 7–14
```

The AI runs entirely on your machine via **LM Studio** — an OpenAI-compatible local API on port 1234. No cloud calls, no API keys, no data leaving your network.

---

## Screenshots

*Screenshots coming soon.*

---

## Source Code

The source code for this project is private. This repository contains only this README.

> Built with Python, FastAPI, React, and a locally hosted LLM via LM Studio.
