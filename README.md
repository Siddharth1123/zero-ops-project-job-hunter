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

## 🏗️ System Architecture

```mermaid
flowchart TD
    User([👤 User / Candidate]) <-->|Interacts via Web Dashboard| WebUI[🖥️ Web App Interface]
    
    subgraph Core Engine [FastAPI Backend]
        WebUI <--> API[🚀 FastAPI Server]
        Cron[⏰ APScheduler Daemon] -->|Triggers Daily Scrape & Digest| Collector[🔎 Scraping Engine]
        
        Collector -->|Fetch Jobs| Sources[🌐 JSearch API + 150+ Career Pages]
        Collector -->|Raw Listings| Scorer[🎯 Scoring & Match Engine]
        
        Scorer -->|Evaluate against Active Profile| ProfileConfig[👤 Profile Configs]
        Scorer -->|Top Ranked Jobs| DMGen[💬 Outreach Generator]
        DMGen -->|Daily 9:00 AM Digest| Emailer[📧 Gmail SMTP Service]
    end

    API <-->|Persist Jobs, Outreaches & Logs| DB[(🗄️ SQLite / Postgres Database)]
    Emailer -->|Delivers Curated List| CandidateInbox([📥 Candidate Email Inbox])
