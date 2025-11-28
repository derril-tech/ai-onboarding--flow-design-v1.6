# 🧪 AI Onboarding Flow Designer
**CrewAI + Mixpanel + Supabase + OpenAI GPT‑4.1-mini**

🌐 **Live App (Vercel):**  
[https://ai-onboarding-flow-design.vercel.app/](https://ai-onboarding-flow-design.vercel.app/)

API & Web are deployed on Railway (see `RAILWAY_SETUP_2025.md`), with the Vercel web app proxying `/api/*` to the Railway API.

> **Design, analyze, and refine SaaS onboarding flows using real analytics and AI agents—without leaving a single React page.**

---

## ✨ Features

### 🎯 Core Experience
- **Crew Lab Conversation** – Chat with three agents (Analyst, UX Writer, PM) about your onboarding goals.
- **LLM‑Powered Analysis** – OpenAI `gpt-4.1-mini` turns Mixpanel funnel + events into senior‑level insights and recommendations.
- **Single-Page Playground** – Conversation, canvas, analytics, and exports all live on one smooth React 19 page—no route hopping.

### 🧩 Flow Canvas & Editing
- **Interactive Flow Canvas** – Visualize the onboarding journey as ordered steps with owners and success rates.
- **Edit Mode** – Add/reorder/delete steps, tweak labels/descriptions/owners, and immediately see the updated flow.
- **Export & Copy** – Export the flow as JSON or React TS code, with one‑click copy for developer handoff.

### 📊 Analytics & Insights
- **Mixpanel Dashboard** – Funnel completion, weakest step, top events, and average completion visualized.
- **Funnel Chart** – Animated bars per step with completion rate and drop‑off reason.
- **CrewAI Verdict** – AI‑generated bullet insights layered on top of Mixpanel data for PM/UX decisions.

### 🗂️ Projects, History & Sync
- **Multi‑Project Support** – Switch between projects with isolated conversations and flows.
- **Conversation History** – Local persistence so sessions survive reloads.
- **Supabase Sync (Optional)** – Persist projects and messages to Supabase for cross‑device continuity.

### 🔗 Sharing & Demo‑Ready UX
- **Shareable Flow Links** – Encode flows into URLs for view‑only sharing with stakeholders.
- **Production‑Grade UI** – Tailwind + shadcn/ui + custom theming for 2025‑level design and dark mode.

---

## 🏗️ Tech Stack

### **Backend (API)**
- **FastAPI (Python 3.11+)**
- **OpenAI SDK** – `gpt-4.1-mini` by default (overridable via `OPENAI_MODEL`).
- **Crew orchestration stub** (`api/crewai_adapter.py`) that uses OpenAI when available, stub otherwise.
- **Mixpanel client** (`api/external/mixpanel_client.py`) for funnels/events.
- **Supabase client** (`api/db/supabase_client.py`) for jobs/messages/projects.

### **Frontend (Web)**
- **Next.js 15.1 (App Router) + React 19**
- **Tailwind CSS + shadcn/ui** with custom theming.
- **Single-page layout** in `web/app/page.tsx`:
  - `HeroSection`, `InsightsSection`, `ExperienceLab`, `TechShowcase`, `IntegrationsSection`, `CTASection`.
- **Hooks**
  - `useAgent(projectId)` – agent runs + polling + state management.
  - `useProjects()` – multi‑project state and selection.
  - `useSupabaseSync()` – optional Supabase sync with graceful fallback.

### **Data & Infra**
- **Supabase (PostgreSQL)** – `onboarding_flow.jobs`, `onboarding_flow.messages`, `onboarding_flow.projects`.
- **Upstash Redis** – (planned) job state, caching, and rate limiting.
- **Deployment**
  - API + Web on **Railway**.
  - Web also on **Vercel** (`https://ai-onboarding-flow-design.vercel.app/`).

---



---

## 👨‍💻 Creator & 🙏 Acknowledgments

- **Created by:** Derril Filemon

- **Thanks to:**
  - OpenAI – LLM backbone (`gpt-4.1-mini`)
  - Supabase – Postgres & auth
  - Upstash – Redis
  - Railway – Hosting for API + Web
  - Vercel – Hosting for Next.js
  - Mixpanel – Analytics data
  - shadcn/ui – Component primitives

---



Made with CrewAI, Mixpanel, and a lot of onboarding love. PRs welcome!

