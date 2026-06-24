# 🚀 SkillHire AI
 A full-stack AI-powered platform that bridges the gap between learning and hiring by helping students **learn, practice, prove skills, and get hired based on real work**, with real-time student + recruiter dashboards.

![License](https://img.shields.io/badge/license-Apache%202.0-blue)
![Stack](https://img.shields.io/badge/stack-React%20%7C%20Supabase%20%7C%20Node-green)
![Status](https://img.shields.io/badge/status-Active-brightgreen)

---

## 1. Project Title & Tagline
SkillHire AI is a proof-based hiring platform that connects student learning workflows directly to recruiter decision workflows through verified skill evidence.

## 2. Problem Statement
Traditional hiring pipelines rely heavily on resumes and self-reported skills, which often do not prove practical ability. Students also face a fragmented journey where learning, validation, and job applications happen in separate tools. This project solves that gap by combining skill-gap analysis, challenge-based verification, project proof submission, and recruiter review in one product. Recruiters can evaluate measurable evidence (status, scores, verified skills, and submissions) instead of claims only. The result is better alignment between student progress and hiring outcomes.

---

## 3. Features

| Feature | Description |
| --- | --- |
| 🧠 Skill Gap Analysis | Identify missing skills based on your target role and current skill set |
| 📄 Resume Analyzer | Extract skills automatically from an uploaded resume (demo-friendly) |
| 📚 Learning Path | Personalized roadmap to close gaps and improve readiness |
| 💻 Skill Lab | Interactive coding challenges to validate skills (with instant feedback) |
| 📂 Projects Marketplace | Apply to portfolio-grade projects and track progress |
| 🧾 GitHub Proof Submission | Submit GitHub links as proof-of-work for verification |
| 📊 Project Scoring | Score submissions for structure/quality and track trends |
| 🧾 Verified Profile | Verified skills aggregate from projects + assessments |
| 🏢 Company Dashboard | Recruiters review applications/submissions and shortlist candidates |
| 🏆 Top Candidates | Auto-ranking based on readiness + verified proof signals |
| 🎯 Job Matching | Suggest jobs and highlight missing skills to improve match |
| 📈 Skill Graph / Progress | Visual progress signals across skills and readiness |

## 4. Tech Stack

### Frontend
- ⚛️ React + TypeScript — Component-based UI
- 🎨 TailwindCSS — Utility-first styling
- ⚡ Vite — Fast dev server + build
- 📊 Recharts — Data visualization
- 🧭 Wouter — Lightweight routing

### Backend
- 🟢 Supabase — Auth + PostgreSQL + Realtime (optional; app runs with demo fallbacks)
- 🗄️ PostgreSQL — Structured storage (via Supabase tables)
- 🟦 Node/Express API — `artifacts/api-server` (dashboard endpoints used by the React client)
- 🧩 Drizzle ORM — DB access layer for API server

## 5. Project Structure

```
Skill-Finder/
├── artifacts/
│   ├── skillhire/                       # React (Vite) app
│   │   ├── src/
│   │   │   ├── pages/                   # Student + company pages (Dashboard, SkillGap, SkillLab, etc.)
│   │   │   ├── components/              # UI + feature components
│   │   │   ├── lib/                     # Demo pipelines + local storage + Supabase integration
│   │   │   └── App.tsx                  # Routing
│   │   ├── .env.example                 # Supabase env template
│   │   └── package.json
│   │
│   └── api-server/                      # Node/Express API (student dashboard endpoints)
│       ├── src/routes/                  # REST routes (e.g. /dashboard/student/:id)
│       └── package.json
│
├── lib/                                 # Shared workspace libs (api client, zod, db)
├── scratch/
│   └── supabase/
│       └── skillhire_core_schema.sql    # Supabase schema (tables + columns used by app)
└── README.md
```

## 6. Installation & Setup

### Prerequisites
- Node.js 18+ (recommended)
- pnpm (`npm i -g pnpm`) (recommended for workspace)
- Supabase project (optional for live data)

### 1. Clone the Repository

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

### 3. API Server (optional but recommended)

```bash
cd artifacts/api-server
pnpm install
pnpm run dev
```

### 4. Supabase Setup (optional for live data)

1) Create a Supabase project  
2) Run the SQL in `scratch/supabase/skillhire_core_schema.sql` in Supabase SQL Editor  
3) Create `artifacts/skillhire/.env.local` based on `.env.example`:

```env
VITE_SUPABASE_URL=your_supabase_url
VITE_SUPABASE_ANON_KEY=your_anon_key
```

The app works without Supabase (demo fallback), but Supabase enables real persistence + realtime review flows.

## 7. How It Works

### 7.1 Student Learning and Readiness Flow
1. **Input**: Student uploads resume or enters profile/goal details.
2. **Processing**: Resume analyzer extracts skills and Skill Gap module computes missing skills and readiness.
3. **Output**: Dashboard and Learning Path show personalized next actions and progress indicators.

### 7.2 Skill Verification and Proof Flow
1. **Input**: Student solves Skill Lab challenges and submits GitHub links for projects/jobs.
2. **Processing**: Challenge evaluator validates required tokens; submission scoring computes quality score and status metadata.
3. **Output**: Verified skills, readiness, and profile proof signals are updated for hiring visibility.

### 7.3 Recruiter Review and Ranking Flow
1. **Input**: Company user reviews applications and submissions.
2. **Processing**: Approve/Reject actions update status in Supabase (or scoped demo overrides when live tables are unavailable).
3. **Output**: Company dashboard updates counts, shortlist state, and top-candidate ranking in near real-time.

---

## 8. Scalability
- Supabase Realtime supports reactive dashboards and scalable Postgres storage
- API server can be containerized and horizontally scaled behind a reverse proxy
- Long-running scoring/analysis can be moved to background jobs (queue/worker) if needed
- Frontend is a static build and can be deployed via CDN (Vercel/Netlify)

## 9. Feasibility
SkillHire AI uses production-grade components (React, Supabase, Postgres, Node/Express) and keeps the architecture simple: a modern frontend + optional realtime persistence. Demo fallbacks ensure the project is always runnable for demos and evaluations.

## 10. Novelty
Most platforms depend on resumes and self-reported skills. SkillHire AI emphasizes **proof-based hiring**:
- Skills validated through coding challenges and real GitHub work
- Recruiters evaluate evidence instead of claims
- Readiness and ranking are based on measurable signals

## 11. Feature Depth
- Skill extraction + skill gap targeting
- Readiness scoring and progress tracking
- Project/job applications with proof links
- Company review pipeline (approve/reject + verified skill awarding)
- Candidate ranking + shortlist workflow
- Dashboard visualizations for trends and decisions

## 12. Ethical Use & Disclaimer
SkillHire AI is intended for **educational and professional development** use.  
Do not submit fake projects, plagiarize work, or misuse the platform to misrepresent skills.

## 13. License
Licensed under the **Apache License 2.0**.

## 14. Author
- **Name**: Abhishek S
- **Email**: abhisakaray@gmail.com
- **GitHub**: [Abhishek-S](https://github.com/Abhishek090406)
