<div align="center">

# 🚀 JobHunter AI

### *Find better jobs. Apply smarter. Automate your career search.*

[![Zerops Deployed](https://img.shields.io/badge/Zerops-Live_App-00C853?style=for-the-badge&logo=zerops&logoColor=white)](https://python-219-8000.ny1.zerops.app)
[![Python 3.12](https://img.shields.io/badge/Python-3.12-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.115-005571?style=for-the-badge&logo=fastapi)](https://fastapi.tiangolo.com/)
[![Zerops Hackathon](https://img.shields.io/badge/Zerops_Hackathon-2026_Entry-blueviolet?style=for-the-badge)](#-hackathon-context--acknowledgements)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)

<br />

[**⚡ VIEW LIVE DEMO**](https://python-219-8000.ny1.zerops.app) &nbsp;•&nbsp; [**📖 INTERACTIVE API DOCS**](https://python-219-8000.ny1.zerops.app/docs) &nbsp;•&nbsp; [**💻 GITHUB REPO**](https://github.com/Siddharth1123/zero-ops-project-job-hunter)

---

</div>

## 📌 Overview

**JobHunter AI** is an intelligent, automated job discovery, matching, and recruiter outreach platform built for software engineers and job seekers.

Instead of wasting hours manually searching job boards, **JobHunter AI** automatically collects job postings across multiple engines and 150+ direct company career pages, scores each job against your target role profile, generates personalized recruiter outreach DMs, and delivers a curated digest to your inbox every morning at 9:00 AM.

<div align="center">
<img src="./assets/dashboard-preview.png" alt="JobHunter AI Dashboard" width="90%">

<sub>Live dashboard — 116 jobs scraped, scored, and sorted by India-friendliness in real time.</sub>
</div>

---

## ⚡ Complete End-to-End Workflow

```text
┌─────────────────┐       ┌──────────────────┐       ┌──────────────────┐       ┌─────────────────┐
│  1. DISCOVERY   │ ────► │   2. MATCHING    │ ────► │   3. OUTREACH    │ ────► │   4. DIGEST     │
│                 │       │                  │       │                  │       │                 │
│ Scrapes JSearch │       │ Scores jobs 0-100│       │ Generates custom │       │ Emails daily 9AM│
│ + 150+ ATS      │       │ against candidate│       │ LinkedIn DMs for │       │ digest with DM  │
│ career portals  │       │ profile criteria │       │ Engineering Leads│       │ templates       │
└─────────────────┘       └──────────────────┘       └──────────────────┘       └─────────────────┘
```

| Stage | What happens |
|---|---|
| 🔍 **Job Collection** | Every day at 9:00 AM IST, background jobs scrape fresh listings from JSearch (LinkedIn, Indeed, Glassdoor) and direct ATS portals (Greenhouse, Lever, Workday). |
| 🎯 **Profile Scoring** | Raw listings are evaluated against your active role profile (keywords, experience level, tech stack, domain signals) to assign a 0–100 match score. |
| 💬 **Outreach Generation** | For top matching jobs, the system generates custom LinkedIn direct message templates targeted at Hiring Managers, Tech Leads, and HR Directors. |
| 📧 **Delivery & Dashboard** | A curated digest email is sent to your inbox while the interactive Web Dashboard updates for easy tracking. |

---

## 🖥️ Live Dashboard in Action

The dashboard gives you an at-a-glance snapshot of your entire pipeline — total jobs scraped, average match score, and a breakdown of India-friendly vs. remote-only postings — with powerful filters by source, score, location, and tech stack.

| Metric | Example Snapshot |
|---|---|
| **Total Jobs Tracked** | 116 |
| **Average Match Score** | 35.5 / 100 |
| 🟢 **India Friendly** | 49 |
| 🟡 **Maybe India** | 60 |
| 🔴 **Not India** | 7 |
| **ArbeitNow Sources** | 84 |
| **RemoteOK Sources** | 16 |
| **Remotive Sources** | 16 |


---

## ✨ Features & Capabilities

| Feature | Description | Status |
|---|---|:---:|
| 🔎 **Multi-Source Scraping** | Aggregates listings daily from major job aggregators + 150+ direct company ATS career portals. | 🟢 Live |
| 🎯 **AI Match Engine** | Scores listings (0–100) based on title relevance, core tech match, experience targets, and domain signals. | 🟢 Live |
| 👤 **Configurable Profiles** | Switch seamlessly between role profiles (Backend Python, Frontend React, Fresher/Entry-Level) via UI. | 🟢 Live |
| 💬 **Outreach Generator** | Generates personalized LinkedIn DMs tailored to candidate bio, achievements, and target roles. | 🟢 Live |
| 📧 **Daily Email Digest** | Sends an automated morning email (9:00 AM IST) featuring top matching jobs with ready-to-send outreach copy. | 🟢 Live |
| 📊 **Application Tracking UI** | Modern web dashboard to review jobs, filter by score/company, manage target profiles, and track application status. | 🟢 Live |

---

## 🛠️ Tech Stack

| Layer | Component | Technology |
|---|---|---|
| ☁️ **Cloud Hosting** | Platform-as-a-Service | Zerops (Python 3.12 Container) |
| ⚙️ **Backend API** | Framework | Python 3.12, FastAPI, Uvicorn |
| 🎨 **Frontend UI** | Web Dashboard | HTML5, Vanilla JavaScript, CSS3 (Glassmorphism Design) |
| 🗄️ **Database** | Persistent Storage | SQLite (Auto-initializing tables) |
| ⏰ **Task Scheduling** | Background Jobs | APScheduler (AsyncIOScheduler) |
| 🔌 **Integrations** | APIs & Gateways | RapidAPI (JSearch API), Gmail SMTP API |

---

## ☁️ Zerops Deployment

This application is deployed and hosted on **Zerops** for the **Zerops Hackathon 2026**.

- 🌐 **Live URL:** [python-219-8000.ny1.zerops.app](https://python-219-8000.ny1.zerops.app)
- ⏱️ **Build Time:** 1 min 7 seconds
- 🏗️ **Architecture:** Python 3.12 container with cached `./vendor` dependency tree and HTTPS routing

<details>
<summary><b>📄 View Production <code>zerops.yml</code></b></summary>

```yaml
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
```

</details>

---

## 🚀 Local Setup & Installation

### Prerequisites
- Python 3.11+
- Git
- Gmail account (with a 16-character App Password)
- RapidAPI key (free subscription to the JSearch API)

### 1. Clone the Repository
```bash
git clone https://github.com/Siddharth1123/zero-ops-project-job-hunter.git
cd zero-ops-project-job-hunter
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Configure Environment Variables
```bash
cp .env.example .env
```

```ini
# RapidAPI JSearch Key
RAPIDAPI_KEY=your_rapidapi_key_here

# Gmail SMTP Digest Settings
SENDER_EMAIL=your-email@gmail.com
SENDER_APP_PASSWORD=your_16_char_app_password
RECIPIENT_EMAIL=candidate-email@gmail.com

# Schedule Settings (IST Timezone)
DAILY_EMAIL_HOUR=9
DAILY_JOBS_COUNT=15
```

### 4. Run the Server Locally
```bash
python -m uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

Then open **http://localhost:8000** in your browser. 🎉

---

## ⚙️ Environment Variables Reference

| Variable | Description | Required |
|---|---|:---:|
| `RAPIDAPI_KEY` | RapidAPI authentication key for JSearch job scraping | ✅ |
| `SENDER_EMAIL` | Sender Gmail address used for daily digests | ✅ |
| `SENDER_APP_PASSWORD` | 16-character Google App Password (*not* your Gmail password) | ✅ |
| `RECIPIENT_EMAIL` | Target email address where the candidate receives daily alerts | ✅ |
| `DAILY_EMAIL_HOUR` | Hour of day (0–23, IST) when the digest is sent | ⬜ Optional |

---

## 🎯 Hackathon Context & Acknowledgements

### Solution Impact

Searching for tech jobs involves hours of manual filtering and writing personalized cold messages. **JobHunter AI automates the entire funnel:**

```
Scrape Listings  ⟶  Match Criteria  ⟶  Draft Outreach  ⟶  Deliver Digest
```

### Original Attribution

This project is adapted from the open-source repository **[job-hunter](https://github.com/replyre)** by *replyre*.

- **Base Framework:** Provided initial concepts for job collection, scoring algorithms, and outreach templates.
- **JobHunter AI Enhancements:** Deployed to the Zerops platform, configured the `zerops.yml` build pipeline, optimized vendor dependency caching, automated environment variables, and built cloud infrastructure for the Zerops Hackathon 2026.

---

## 👨‍💻 Author

**Siddharth Jain**

[![GitHub](https://img.shields.io/badge/GitHub-@Siddharth1123-181717?style=flat-square&logo=github)](https://github.com/Siddharth1123)
[![Repo](https://img.shields.io/badge/Repo-zero--ops--project--job--hunter-blue?style=flat-square&logo=github)](https://github.com/Siddharth1123/zero-ops-project-job-hunter)
[![Live App](https://img.shields.io/badge/Live_App-Zerops-00C853?style=flat-square&logo=zerops)](https://python-219-8000.ny1.zerops.app)

---

## 📄 License

This project retains all licensing and attribution terms from the original project under the **MIT License**.

<div align="center">

⭐ *If you found this project useful, consider giving it a star!* ⭐

</div>
