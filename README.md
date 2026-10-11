# 🚀 LeadRank AI

**AI-powered lead ranking and scoring system that helps sales teams identify which leads to contact first.**

LeadRank takes a raw CSV lead list, cleans and validates the data, removes duplicates, evaluates leads against an **Ideal Customer Profile (ICP)**, and produces a ranked list with scores, explanations, and suggested outreach openers.

---

## ✨ Key Features

- 📥 **CSV Lead Upload** — Import lead lists from different sources.
- 🧹 **Data Cleaning & Normalization** — Standardizes company names, domains, employee counts, and other fields.
- ✅ **Lead Validation** — Detects invalid emails, shared inboxes, personal email providers, and invalid domains.
- 🔄 **Duplicate Detection** — Identifies duplicate leads using email, domain, and person information.
- 🎯 **ICP-Based Scoring** — Scores leads from **0–100** based on your Ideal Customer Profile.
- 🤖 **AI-Powered Scoring** — Uses Claude API for intelligent lead evaluation.
- ⚡ **Rule-Based Fallback** — Continues scoring even when the AI API is unavailable.
- 💡 **Score Explanation** — Provides a reason behind each lead's score.
- 💬 **AI-Generated Openers** — Generates a short personalized opening line for sales outreach.
- 🔎 **Search & Filtering** — Filter leads by score, tier, and search terms.
- 📊 **Lead Summary** — View hot, warm, and cold lead statistics.
- 📤 **CSV Export** — Export ranked leads or HubSpot-compatible CSV files.
- 💾 **Score Caching** — Avoids unnecessary AI API calls for unchanged leads.

---

## 🎯 Lead Scoring

LeadRank evaluates leads using multiple factors:

| Factor | Weight |
|---|---:|
| Industry | 30% |
| Company Size | 25% |
| Title / Seniority | 25% |
| Data Quality | 10% |
| Region | 10% |

### Lead Tiers

| Score | Tier |
|---:|---|
| 75–100 | 🔥 Hot |
| 50–74 | 🟡 Warm |
| 0–49 | 🔵 Cold |

---

## 🏗️ Architecture

```text
CSV Upload
    │
    ▼
Parse & Normalize
    │
    ▼
Validate Lead Data
    │
    ▼
Remove Duplicates
    │
    ▼
Store in PostgreSQL
    │
    ▼
Apply ICP
    │
    ▼
AI / Rule-Based Scoring
    │
    ▼
Generate Score + Reason + Opener
    │
    ▼
Rank & Filter Leads
    │
    ▼
Dashboard / CSV Export
```

---

## 🛠️ Tech Stack

### Frontend
- React 18
- Vite
- Tailwind CSS 4

### Backend
- Node.js
- Express.js

### Database
- PostgreSQL
- PGlite for local zero-setup development

### AI
- Anthropic Claude API
- Rule-based fallback scoring

### Deployment
- Vercel
- Render

---

## 📁 Project Structure

```text
leadrank/
│
├── client/
│   ├── src/
│   │   ├── components/
│   │   │   ├── LeadPanel.jsx
│   │   │   ├── LeadTable.jsx
│   │   │   ├── IcpForm.jsx
│   │   │   ├── SummaryBar.jsx
│   │   │   └── UploadZone.jsx
│   │   ├── api.js
│   │   ├── App.jsx
│   │   └── main.jsx
│   └── package.json
│
├── server/
│   ├── src/
│   │   ├── db/
│   │   ├── routes/
│   │   ├── services/
│   │   ├── test/
│   │   ├── app.js
│   │   └── index.js
│   ├── package.json
│   └── .env.example
│
├── data/
│   └── sample_leads.csv
│
├── scripts/
│   └── make_sample.mjs
│
├── package.json
├── .gitignore
└── README.md
```

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/leadrank-ai.git
cd leadrank-ai
```

### 2. Install dependencies

```bash
npm run install:all
```

### 3. Configure environment variables

Create the server environment file:

```bash
cp server/.env.example server/.env
```

Add your API key if you want to use AI-powered scoring:

```env
ANTHROPIC_API_KEY=your_api_key_here
```

A rule-based scorer is available when no API key is configured.

### 4. Start the backend

```bash
npm run dev:server
```

Backend:

```text
http://localhost:4000
```

### 5. Start the frontend

In another terminal:

```bash
npm run dev:client
```

Frontend:

```text
http://localhost:5173
```

---

## 🧪 Testing

Run the test suite:

```bash
npm test
```

The tests cover:

- CSV parsing
- Data validation
- Duplicate detection
- Lead scoring
- Upload workflow
- Lead ranking
- CSV export

---

## 🔌 API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/icp` | Save an Ideal Customer Profile |
| POST | `/api/uploads` | Upload and process a CSV |
| POST | `/api/uploads/:id/score` | Start lead scoring |
| GET | `/api/uploads/:id/summary` | Get scoring progress |
| GET | `/api/leads` | Get ranked and filtered leads |
| GET | `/api/uploads/:id/export.csv` | Export leads |

---

## 💡 Why LeadRank?

Finding thousands of leads is no longer the biggest challenge.

The real challenge is knowing:

> **Which leads should a sales representative contact first?**

LeadRank focuses on **lead prioritization**, combining data quality, ICP matching, company characteristics, seniority, and AI-assisted reasoning to help sales teams spend more time on high-potential opportunities.

---

## 🔮 Future Improvements

- 🔍 Live company enrichment
- 💰 Funding and revenue enrichment
- 🧑‍💻 Technology-stack detection
- 📈 Machine-learning-based scoring from historical deals
- 🔐 Authentication and user workspaces
- 📊 Advanced analytics dashboard
- 🔗 CRM integrations
- 📧 Automated personalized outreach
- 🤖 Autonomous AI sales research agent

---

## 🔒 Security & Responsible Use

LeadRank is designed to process lead information that you are authorized to use.

Users are responsible for complying with applicable privacy, data-protection, and outreach regulations, including regulations such as **GDPR** and **CAN-SPAM** where applicable.

Never commit API keys, passwords, database credentials, or other secrets to the repository.

---

## 👨‍💻 Author

**Pradeep Rathod**

AI/ML Student | AI Agent Builder | Data Science Enthusiast

---

## ⭐ Support

If you find this project useful, consider giving the repository a ⭐ on GitHub.

Contributions, suggestions, and improvements are welcome!
