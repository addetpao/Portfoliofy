Portfoliofy

Turn your resume into a dynamic, professional portfolio website — instantly.

Portfoliofy lets job seekers upload a resume (PDF, DOCX, TXT, or LinkedIn export) and automatically generates a polished, multi-page portfolio site. AI powers resume parsing, smart improvements, and effortless customization.

✨ Features

Instant Portfolio Generation – Upload a resume → get a live portfolio site under your domain.

AI Resume Improvements – ATS optimization, stylistic polish, and tailored job targeting.

Multi-Page Templates – Choose from corporate or creative themes.

Custom Domains – Map a personal domain directly through GoDaddy/Namecheap.

Analytics Dashboard – Track visits, sources, downloads, and contact submissions.

Private by Default – Portfolios are unlisted until you choose to go public.

🏗️ Tech Stack

Frontend Web: Next.js + Tailwind + shadcn/ui

Mobile: React Native (lite for free, full parity for Pro)

Backend: Node.js + Express/Fastify (REST/GraphQL APIs)

Storage & Auth: Supabase or Firebase

AI/Parsing: OpenAI / Anthropic APIs + Resume Parsing APIs

Payments: Stripe (subscriptions + domain purchases)

Domains: GoDaddy/Namecheap API

Hosting: Vercel (web), App/Play Store (mobile)

🚀 Getting Started

Clone the repo:

git clone https://github.com/your-username/portfoliofy.git
cd portfoliofy


Install dependencies (using pnpm workspaces):

pnpm install


Run apps:

pnpm dev:web     # start Next.js web app
pnpm dev:api     # start API server
pnpm dev:mobile  # start React Native app


Copy .env.example → .env.local and add required API keys.

📖 Roadmap (MVP → Future)

✅ Resume upload (PDF/DOCX/TXT/LinkedIn)

✅ Auto portfolio generation (3–5 templates)

✅ Pro plan ($12.99/mo) with AI resume improvements + analytics

🔜 Inline editing on live portfolios

🔜 Template marketplace

🔜 Enterprise/team accounts

📜 License

This project is licensed under the MIT License
