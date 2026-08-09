<div align="center">

# 🚀 JobHunter AI
### *Find better jobs. Apply smarter. Automate your career search.*

[![Python 3.11+](https://img.shields.io/badge/Python-3.11+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)](https://fastapi.tiangolo.com/)
[![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)
[![Hackathon Entry](https://img.shields.io/badge/Hackathon-Project_2026-brightgreen?style=for-the-badge)](#-hackathon-context--acknowledgements)

[**🌐 View Live Demo**](https://sids-job-hunter.onrender.com) | [**📖 Explore Documentation**](#-getting-started) | [**🐛 Report Issue**](https://github.com/Siddharth1123/sid-s-job-hunter/issues)

---

</div>

## 📌 Overview

**JobHunter AI** is an intelligent job discovery, scoring, and automated outreach platform built for software engineers and job seekers. 

Instead of manually spending hours filtering through thousands of irrelevant job board listings, **JobHunter AI** automatically collects job postings across multiple job engines and 150+ company career pages, scores each posting against your custom candidate profile, generates personalized recruiter outreach DMs, and delivers a curated digest to your inbox every morning.

---

## ✨ Key Features

| Feature | Description |
| :--- | :--- |
| 🔎 **Automated Job Discovery** | Aggregates listings daily from major job engines (JSearch, LinkedIn, Indeed, Glassdoor) + 150+ direct company ATS pages (Greenhouse, Lever, Workday). |
| 🎯 **AI Match Scoring** | Evaluates jobs against your active candidate profile (title keywords, tech stack, experience level, domain signals) and assigns a 0-100 match score. |
| 👤 **Multi-Profile Management** | Switch seamlessly between different job target profiles (e.g., *Backend Python*, *Frontend React*, or *Entry-Level/Fresher*) without touching code. |
| 💬 **Automated Recruiter Outreach** | Generates tailored LinkedIn DM templates for Eng Managers, CTOs, and HR leads per company based on profile templates. |
| 📧 **Daily Email Digest** | Sends a curated morning email digest (at 9:00 AM IST) featuring top matching jobs with ready-to-send outreach messages. |
| 📊 **Application Dashboard** | Full-featured web interface to search, filter, track application status, manage profiles, and monitor scraper API usage. |

---

1. **Job Collection:** Every day at 9:00 AM IST, background jobs scrape fresh listings from JSearch (LinkedIn, Indeed, Glassdoor) and direct ATS portals (Greenhouse, Lever, Workday).
2. **Profile Scoring:** Raw listings are evaluated against your active role profile (keywords, experience level, tech stack, domain signals) to assign a 0–100 match score.
3. **Outreach DM Generation:** For top matching jobs, the system generates custom LinkedIn direct message templates targeted at Hiring Managers, Tech Leads, and HR Directors.
4. **Email Delivery & Dashboard:** A curated digest email is sent to your inbox while updating your interactive Web Dashboard for tracking.

---

## ✨ Features & Capabilities

| Feature | Description |
| :--- | :--- |
| 🔎 **Multi-Source Scraping** | Aggregates listings daily from major job aggregators + 150+ direct company ATS career portals. |
| 🎯 **AI Match Engine** | Scores listings (0-100) based on title relevance, core tech match, experience targets, and domain signals. |
| 👤 **Configurable Profiles** | Switch seamlessly between role profiles (*Backend Python*, *Frontend React*, *Fresher/Entry-Level*) via UI. |
| 💬 **Outreach Generator** | Generates personalized LinkedIn DMs tailored to candidate bio, achievements, and target roles. |
| 📧 **Daily Email Digest** | Sends an automated morning email (9:00 AM IST) featuring top matching jobs with ready-to-send outreach copy. |
| 📊 **Application Tracking UI** | Modern web dashboard to review jobs, filter by score/company, manage target profiles, and track application status. |

---

## 🏗️ System Architecture

```mermaid
flowchart TD
    Candidate([👤 Candidate / User]) <-->|Access Dashboard| WebUI[🖥️ Web App Interface]

    subgraph Zerops Cloud Infrastructure [☁️ Zerops Python 3.12 Service]
        WebUI <--> API[🚀 FastAPI Backend Engine]
        Scheduler[⏰ APScheduler Daemon] -->|Triggers Daily Run| Scraper[🔎 Scraping Engine]
        
        Scraper -->|Scrape API| JSearch[🌐 JSearch API]
        Scraper -->|Crawl Career Pages| CompanyATS[🏢 150+ Direct Company Portals]
        
        Scraper -->|Raw Jobs| Scoring[🎯 Profile Scoring Engine]
        Scoring <-->|Fetch Active Profile| Profiles[(👤 Active Profile Config)]
        
        Scoring -->|Top Ranked Jobs| DMGen[💬 Outreach Template Engine]
        DMGen -->|Daily 9:00 AM IST| Mailer[📧 Gmail SMTP Gateway]
    end

    API <-->|Persist Jobs, Outreaches & Logs| DB[(🗄️ SQLite Database)]
    Mailer -->|Delivers Curated Job Digest| Inbox([📥 Candidate Email Inbox])


🛠️ Tech Stack
Component	Technology
Hosting & Cloud Platform	Zerops (Managed Python 3.12 Runtime)
Backend Framework	Python 3.12, FastAPI, Uvicorn
Frontend UI	HTML5, JavaScript, Vanilla CSS (Glassmorphism design)
Database	SQLite (Automated table migrations)
Task Scheduler	APScheduler (AsyncIOScheduler)
APIs & Integrations	RapidAPI (JSearch), Gmail SMTP API
Configuration	zerops.yml, python-dotenv


☁️ Zerops Deployment & Configuration
This application is deployed and hosted on Zerops for the Zerops Hackathon 2026.

Deployment Architecture
Runtime Service: Python 3.12 Managed Container
Environment Configuration: Managed via zerops.yml and Zerops Secret Environment Variables
Public Access: HTTPS Subdomain via Zerops HTTP Routing Gateway (https://python-219-8000.ny1.zerops.app)
zerops.yml Configuration
yaml


zerops:
  - setup: python
    build:
      base: python@3.12
      buildCommands:
        - pip install --target=./vendor -r requirements.txt
      deployFiles:
        - ./
        - ./vendor
      cache:
        - vendor
    run:
      base: python@3.12
      envVariables:
        PYTHONPATH: /var/www/vendor
      ports:
        - port: 8000
          httpSupport: true
      start: python3 -m uvicorn main:app --host 0.0.0.0 --port 8000
🚀 Local Setup & Installation
Prerequisites
Python 3.11+
Git
Gmail Account (with an App Password)
RapidAPI Key (Free subscription to JSearch API)
1. Clone the Repository
bash


git clone https://github.com/Siddharth1123/zero-ops-project-job-hunter.git
cd zero-ops-project-job-hunter
2. Install Dependencies
bash


pip install -r requirements.txt
3. Environment Variables
Create a .env file in the root directory:

bash


cp .env.example .env
Configure your credentials:

ini


# RapidAPI JSearch Key
RAPIDAPI_KEY=your_rapidapi_key_here
# Gmail SMTP Digest Settings
SENDER_EMAIL=your-email@gmail.com
SENDER_APP_PASSWORD=your_16_char_app_password
RECIPIENT_EMAIL=candidate-email@gmail.com
# Timing (IST Timezone)
DAILY_EMAIL_HOUR=9
DAILY_JOBS_COUNT=15
4. Run Locally
bash


python -m uvicorn main:app --host 0.0.0.0 --port 8000 --reload
Open http://localhost:8000 in your browser.

⚙️ Environment Variables Summary
Key	Description	Required
RAPIDAPI_KEY	RapidAPI key subscribed to JSearch	Yes
SENDER_EMAIL	Gmail address used to send daily digests	Yes
SENDER_APP_PASSWORD	16-character Gmail App Password	Yes
RECIPIENT_EMAIL	Candidate inbox where digests are delivered	Yes
DAILY_EMAIL_HOUR	Scheduled hour in IST (default: 9 for 9:00 AM)	Optional
🎯 Hackathon Context & Acknowledgements
Project Goal
Finding a job in today's tech market involves overwhelming manual searching, filtering, and writing cold DMs. JobHunter AI transforms this 2-hour daily struggle into a 10-minute automated morning routine:

Scrape
⟶
Score
⟶
Generate Outreach
⟶
Deliver Digest
Scrape⟶Score⟶Generate Outreach⟶Deliver Digest
Original Project Attribution
This repository is adapted from the open-source project job-hunter by replyre.

Base Features: Job collection, initial scoring logic, profile configuration templates.
JobHunter AI Enhancements: Deployed to Zerops Platform, configured zerops.yml build pipeline, optimized vendor dependency caching, automated environment variables, and created end-to-end cloud infrastructure for the Zerops Hackathon 2026.


👨‍💻 Author
Siddharth Jain
GitHub: @Siddharth1123
Project Repository: Siddharth1123/zero-ops-project-job-hunter
Live App: https://python-219-8000.ny1.zerops.app

📄 License
This project retains all licensing and attribution terms from the original project under the MIT License.
