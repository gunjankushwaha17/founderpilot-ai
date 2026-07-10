# Product Requirement Document (PRD)

**Project Name:** FounderPilot AI
**Target Audience:** Aspiring Entrepreneurs, Indie Hackers,Students , Anyone.
**Author:** Gunjan Kushwaha
**Status:** Ready for Implementation
**Tech Stack:** Antigravity (Framework), Next.js / Tailwind CSS (Frontend Layout), Google Gemini / OpenAI API (AI Intelligence), Supabase/PostgreSQL (Optional Database)

---

## 1. Executive Summary & Objective

FounderPilot AI is an AI-powered "Co-Founder App" that transforms a raw, single-sentence startup idea into a comprehensive, interactive business validation report and roadmap in under 60 seconds.

Instead of building a cluttered multi-agent system that takes weeks to debug, this product leverages Structured AI Orchestration via Antigravity. It packs the punch of an enterprise-grade SaaS platform into a tight, responsive, single-page application that demonstrates product thinking, clean UI engineering, and practical AI implementation.

---

## 2. Core User Features (Scope for MVP)

### Feature 1: The Launchpad (Input Form)

A clean, centralized form where the user inputs the foundational constraints of their startup idea.

**Fields Required:**

- **Startup Idea:** (Textarea, max 500 characters)
- **Target Audience:** (Input text, e.g., "School Teachers", "College Students")
- **Geographic Market:** (Dropdown/Combobox, default: "India")
- **Starting Budget:** (Input number/currency select, default in ₹ Lakhs)
- **Execution Timeline:** (Slider or Select: 3 Months, 6 Months, 12 Months)

### Feature 2: The Core Validation Matrix (The Dashboard)

Once the user clicks "Validate Idea", the app hides the form, shows a high-quality loading skeleton, and populates 4 core visual cards from a single structured JSON response:

- **Card A: Strategy & Innovation** — Displays a calculated "Innovation Score" (out of 10) and a beautifully styled 4-quadrant SWOT Analysis grid.
- **Card B: The Product Blueprint (MVP)** — Lists features categorized strictly into a MoSCoW Framework (Must-Have vs. Nice-to-Have) tailored to their execution timeline.
- **Card C: Tech Stack Recommendation** — A clean list of recommended tools (Frontend, Backend, Database, AI Tools) based on their budget and timeline constraints.
- **Card D: Financial & Risk Breakdown** — A year-1 estimated cost breakdown (Development, Cloud, Marketing) paired with a high/medium risk evaluation and an actionable mitigation strategy.

### Feature 3: Context-Aware Co-Founder Chat

A sticky right-hand sidebar chat interface.

Once the report is generated, the user can instantly chat with their "AI Co-Founder."

**The Magic:** The chat system automatically holds the generated report in its context background. If the user asks "How do I market this?", the AI dynamically reads the budget and target audience from the report to answer accurately.

---

## 3. System Architecture & Data Flow

Antigravity handles the bridge between your UI and the AI engine cleanly. The data flows sequentially like this:

```
[User Form Input]
       │
       ▼
[Antigravity Server Action] ───> Sends Input Data + Strict JSON Schema to LLM
       │
       ▼
[Structured LLM JSON Response]
       │
       ▼
[State Manager] ───────────────> Hydrates Dashboard UI Components & Saves to Chat Context
```

---

## 4. Technical Specifications & JSON Schema

To prevent the AI from generating broken, unpredictable text that cracks your UI layout, you must enforce a strict JSON response. This is the exact schema you will feed into the Antigravity system:

```json
{
  "innovationScore": 8.5,
  "swotAnalysis": {
    "strengths": ["Automates repetitive tasks", "Low cost of initial delivery"],
    "weaknesses": ["High dependency on user trust", "Initial data cold-start"],
    "opportunities": ["Rapidly growing digital adoption", "Underserved regional markets"],
    "threats": ["Low barrier to entry for clones", "Platform risk from big tech"]
  },
  "mvpBlueprint": {
    "mustHave": ["User authentication", "Core AI content generator", "Export to PDF"],
    "niceToHave": ["Interactive user analytics", "Multi-language support"]
  },
  "techStack": {
    "frontend": "Next.js + Tailwind CSS",
    "backend": "Antigravity Server Actions",
    "database": "Supabase PostgreSQL",
    "aiLayer": "Gemini 1.5 Flash via Structured Outputs"
  },
  "financials": {
    "devCostEstimate": "₹1,50,000",
    "monthlyOperationalCost": "₹5,000",
    "marketingAllocation": "₹50,000"
  },
  "riskAssessment": {
    "level": "Medium",
    "primaryRisk": "High customer acquisition costs in the education sector.",
    "mitigation": "Partner with independent coaching centers first before targeting large schools."
  }
}
```

## 5. Non-Functional Requirements (Resume Boosters)

- **UI/UX Snappiness:** The transition from form submission to dashboard must feature a themed skeleton loader so the user never wonders if the app crashed.
- **Mobile Responsiveness:** The dashboard should gracefully stack into a single vertical column on mobile screens, proving your CSS/Tailwind fluency.
- **Error Resilience:** If the AI API times out or fails, the Antigravity action must capture the error and display a user-friendly message rather than crashing the page.

---

## 6. What to Study Once It Is Built

After your AI tools build this successfully and it is running live on Vercel, spend 1–2 hours studying these terms so you can talk about them confidently to recruiters:

- **JSON Schema Validation:** How the application ensures data integrity between an AI output and a React component.
- **Server Actions vs. API Endpoints:** How Antigravity handles backend logic securely without exposing private API keys to the browser.
- **State Management:** How the application passes the startup report data down into the chat component to serve as context.
