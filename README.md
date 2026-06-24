# 🚀 SkillHire AI

A full-stack platform that bridges the gap between learning and hiring by helping students learn, practice, prove skills, and get hired based on real work — with real-time student and recruiter dashboards.

![License](https://img.shields.io/badge/license-Apache%202.0-blue)
![Stack](https://img.shields.io/badge/stack-React%20%7C%20Node%20%7C%20Supabase-informational)
![Status](https://img.shields.io/badge/status-active-success)

---

## Table of Contents

- [Problem Statement](#problem-statement)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Installation & Setup](#installation--setup)
- [How It Works](#how-it-works)
- [Scalability](#scalability)
- [Feasibility](#feasibility)
- [Novelty](#novelty)
- [Feature Depth](#feature-depth)
- [Ethical Use & Disclaimer](#ethical-use--disclaimer)
- [License](#license)
- [Author](#author)

---

## Problem Statement

Traditional hiring pipelines rely heavily on resumes and self-reported skills, which often fail to prove practical ability. Students also face a fragmented journey, where learning, validation, and job applications happen across separate, disconnected tools.

SkillHire AI solves this by combining skill-gap analysis, challenge-based verification, project proof submission, and recruiter review into a single product. Recruiters evaluate measurable evidence — status, scores, verified skills, and submissions — instead of unverified claims. The result is tighter alignment between student progress and actual hiring outcomes.

## Features

| Feature | Description |
|---|---|
| 🧠 Skill Gap Analysis | Identifies missing skills based on a student's target role and current skill set |
| 📄 Resume Analyzer | Extracts skills automatically from an uploaded resume (demo-friendly) |
| 📚 Learning Path | Personalized roadmap to close gaps and improve readiness |
| 💻 Skill Lab | Interactive coding challenges that validate skills with instant feedback |
| 📂 Projects Marketplace | Apply to portfolio-grade projects and track progress |
| 🧾 GitHub Proof Submission | Submit GitHub links as proof-of-work for verification |
| 📊 Project Scoring | Scores submissions for structure and quality, and tracks trends over time |
| 🧾 Verified Profile | Aggregates verified skills from completed projects and assessments |
| 🏢 Company Dashboard | Lets recruiters review applications and submissions, and shortlist candidates |
| 🏆 Top Candidates | Auto-ranks candidates based on readiness and verified proof signals |
| 🎯 Job Matching | Suggests jobs and flags missing skills to improve match quality |
| 📈 Skill Graph / Progress | Visualizes progress across skills and overall readiness |

## Tech Stack

**Frontend**
- ⚛️ React + TypeScript — component-based UI
- 🎨 Tailwind CSS — utility-first styling
- ⚡ Vite — dev server + build tooling
- 📊 Recharts — data visualization
- 🧭 Wouter — lightweight routing

**Backend**
- 🟢 Supabase — auth, PostgreSQL, and realtime (optional; app runs on demo fallbacks without it)
- 🗄️ PostgreSQL — structured storage via Supabase tables
- 🟦 Node.js / Express — API server for dashboard endpoints consumed by the React client
- 🧩 Drizzle ORM — database access layer for the API server

## Project Structure

```
Skill-Finder/
├── artifacts/
│   ├── skillhire/                 # React (Vite) app
│   │   ├── src/
│   │   │   ├── pages/             # Student + company pages (Dashboard, SkillGap, SkillLab, etc.)
│   │   │   ├── components/        # UI + feature components
│   │   │   ├── lib/                # Demo pipelines + local storage + Supabase integration
│   │   │   └── App.tsx             # Routing
│   │   ├── .env.example            # Supabase env template
│   │   └── package.json
│   │
│   └── api-server/                 # Node/Express API (student dashboard endpoints)
│       ├── src/routes/              # REST routes (e.g. /dashboard/student/:id)
│       └── package.json
│
├── lib/                             # Shared workspace libs (API client, zod, db)
├── scratch/
│   └── supabase/
│       └── skillhire_core_schema.sql   # Supabase schema (tables + columns used by the app)
└── README.md
```

## Installation & Setup

### Prerequisites

- Node.js 18+
- pnpm (`npm i -g pnpm`) — recommended for workspace management
- A Supabase project — optional, for live data

### 1. Clone the repository

```bash
git clone https://github.com/Ashvanth-M/skillhire-ai.git
cd Skill-Finder
```

### 2. Frontend (SkillHire UI)

```bash
cd artifacts/skillhire
npm install
npm run dev
```

Frontend runs at `http://localhost:5173`

### 3. API server (optional, recommended)

```bash
cd artifacts/api-server
pnpm install
pnpm run dev
```

### 4. Supabase setup (optional, for live data)

1. Create a Supabase project.
2. Run the SQL in `scratch/supabase/skillhire_core_schema.sql` in the Supabase SQL Editor.
3. Create `artifacts/skillhire/.env.local` based on `.env.example`:

```env
VITE_SUPABASE_URL=your_supabase_url
VITE_SUPABASE_ANON_KEY=your_anon_key
```

> The app works without Supabase via demo fallback data, but Supabase enables real persistence and realtime review flows.

## How It Works

### Student Learning & Readiness Flow
- **Input:** Student uploads a resume or enters profile/goal details.
- **Processing:** The resume analyzer extracts skills, and the Skill Gap module computes missing skills and a readiness score.
- **Output:** Dashboard and Learning Path surface personalized next actions and progress indicators.

### Skill Verification & Proof Flow
- **Input:** Student solves Skill Lab challenges and submits GitHub links for projects/jobs.
- **Processing:** The challenge evaluator validates required outputs; submission scoring computes a quality score and status metadata.
- **Output:** Verified skills, readiness, and profile proof signals update for hiring visibility.

### Recruiter Review & Ranking Flow
- **Input:** Company user reviews applications and submissions.
- **Processing:** Approve/reject actions update status in Supabase (or scoped demo overrides when live tables aren't available).
- **Output:** Company dashboard updates application counts, shortlist state, and top-candidate ranking in near real time.

## Scalability

- Supabase Realtime supports reactive dashboards and scalable Postgres storage.
- The API server can be containerized and horizontally scaled behind a reverse proxy.
- Long-running scoring/analysis logic can be moved to background jobs (queue/worker) as load grows.
- The frontend is a static build and can be deployed via CDN (Vercel/Netlify).

## Feasibility

SkillHire AI is built on production-grade components — React, Supabase, Postgres, Node/Express — and keeps the architecture intentionally simple: a modern frontend plus optional realtime persistence. Demo fallbacks ensure the project is always runnable for demos and evaluations, even without a live Supabase connection.

## Novelty

Most platforms depend on resumes and self-reported skills. SkillHire AI is built around proof-based hiring instead:

- Skills are validated through coding challenges and real GitHub submissions, not self-assessment.
- Recruiters evaluate evidence rather than claims.
- Readiness and candidate ranking are based on measurable signals, not resume keywords.

## Feature Depth

- Skill extraction and skill-gap targeting
- Readiness scoring and progress tracking over time
- Project/job applications with proof links
- Company review pipeline (approve/reject + verified-skill awarding)
- Candidate ranking and shortlist workflow
- Dashboard visualizations for trends and decisions

## Ethical Use & Disclaimer

SkillHire AI is intended for educational and professional development use. Do not submit fake projects, plagiarize work, or misuse the platform to misrepresent skills.

## License

Licensed under the [Apache License 2.0](LICENSE).

## Author

**Abhishek S**
📧 abhisakaray@gmail.com
🔗 [GitHub — Abhishek-S](https://github.com/Abhishek090406)
