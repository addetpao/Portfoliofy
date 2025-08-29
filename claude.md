# PROJECT_GUIDE.md

This file provides comprehensive guidance for contributors working on the **Resume → Portfolio Website & App** project.

## 🌍 Core Development Philosophy

- **KISS (Keep It Simple, Stupid):** Prioritize simplicity in design and code.  
- **YAGNI (You Aren’t Gonna Need It):** Only build features when needed.  
- **Fail Fast:** Validate early, raise errors quickly.  
- **Single Responsibility:** Each component/service should have one clear purpose.  
- **Open/Closed Principle:** Components should be open for extension but closed for modification.  

---

## 🧱 Project Architecture & Structure

This is a **full-stack TypeScript project** with Next.js (web), React Native (mobile), and Node.js backend services.

### Monorepo Layout

```
/apps
  /web              # Next.js frontend (dashboard + portfolio rendering)
  /mobile           # React Native app (lite for free, full parity for Pro)
  /api              # Node.js backend (REST/GraphQL, AI resume parsing, payments)

/packages
  /ui               # Shared UI components (Tailwind + shadcn/ui)
  /types            # Shared TypeScript types
  /utils            # Reusable helpers (validation, logging, analytics)

/infra
  /scripts          # DevOps, CI/CD configs
  /terraform        # Infra as code (if needed for cloud setup)

/tests
  /e2e              # End-to-end Playwright tests
```

### Key Technologies

- **Frontend (Web):** Next.js, TailwindCSS, shadcn/ui  
- **Mobile:** React Native  
- **Backend:** Node.js + Express/Fastify (with REST/GraphQL APIs)  
- **AI/Parsing:** OpenAI/Anthropic APIs + Resume parsing APIs  
- **Storage:** Supabase or Firebase (files, auth, DB)  
- **Payments:** Stripe (subs + domain purchases)  
- **Domains:** GoDaddy/Namecheap API  
- **Hosting:** Vercel (web), App/Play Store (mobile)  

---

## 🛠️ Development Environment

### Package Management

This project uses **pnpm** for workspaces:

```bash
# Install dependencies
pnpm install

# Run web
pnpm --filter web dev

# Run mobile
pnpm --filter mobile start

# Run backend
pnpm --filter api dev
```

### Scripts

```bash
# Run all tests
pnpm test

# Linting
pnpm lint

# Type checking
pnpm typecheck

# Format
pnpm format

# Build all apps
pnpm build
```

---

## 📋 Style & Conventions

### TypeScript Style Guide

- **Line length:** 100 chars (ESLint rule)  
- **Strings:** Use double quotes  
- **Semicolons:** Required  
- **Imports:** Absolute imports from `/src` preferred  
- **Type Safety:** Always use TypeScript types/interfaces  

### Naming

- **Variables/functions:** `camelCase`  
- **Components/Classes:** `PascalCase`  
- **Constants:** `UPPER_SNAKE_CASE`  
- **File names:** `kebab-case.tsx`  

### Docstrings & Comments

Use TSDoc-style comments for functions and classes:

```ts
/**
 * Generate portfolio URL for a user
 * @param userId - unique user identifier
 * @returns portfolio URL as string
 */
function generatePortfolioUrl(userId: string): string { ... }
```

---

## 🧪 Testing Strategy

- **Unit tests:** Vitest/Jest for logic, React Testing Library for components  
- **Integration tests:** API + DB interactions  
- **E2E tests:** Playwright for workflows (resume upload → portfolio live)  
- **Coverage target:** 80%+ critical path  

---

## 🚨 Error Handling & Logging

- Use **Zod** for validation of inputs/outputs.  
- Standardized error objects: `{ code, message, details }`.  
- Use **structured logging** with Winston or Pino.  

Example:

```ts
logger.info("portfolio_generated", {
  userId,
  templateId,
  domain: url,
});
```

---

## 🔧 Configuration Management

- Env vars managed via `.env` + `@t3-oss/env-nextjs`  
- Required vars:  
  - STRIPE_SECRET_KEY  
  - SUPABASE_URL, SUPABASE_KEY  
  - OPENAI_API_KEY  
  - GODADDY_API_KEY / NAMECHEAP_API_KEY  

---

## 🏗️ Data Models

### Example (Prisma schema if using Supabase/Postgres):

```prisma
model User {
  id             String   @id @default(cuid())
  email          String   @unique
  name           String?
  plan           String   @default("free")
  portfolios     Portfolio[]
  createdAt      DateTime @default(now())
  updatedAt      DateTime @updatedAt
}

model Portfolio {
  id          String   @id @default(cuid())
  userId      String
  templateId  String
  domain      String?
  isPublic    Boolean  @default(false)
  visits      Int      @default(0)
  createdAt   DateTime @default(now())
  updatedAt   DateTime @updatedAt
}
```

---

## 🔄 Git Workflow

- `main` → production-ready  
- `dev` → integration branch  
- `feature/*` → new features  
- `fix/*` → bug fixes  
- `docs/*` → documentation updates  

Commit format (Conventional Commits):

```
feat(auth): add Google login
fix(api): resolve resume parsing error
```

---

## 🛡️ Security Best Practices

- No secrets in repo — use env vars  
- JWT auth with refresh tokens  
- Stripe PCI compliance for payments  
- Input validation everywhere (Zod)  
- HTTPS enforced  

---

## 📊 Monitoring & Observability

- Logging: Pino/Winston  
- Error tracking: Sentry  
- Metrics: Prometheus + Grafana (future)  

---

## 🚀 Performance Considerations

- Portfolio load < 2s (CDN caching)  
- Resume parsing < 10s (queue + async workers)  
- Optimize React components with memoization  

---

## 📚 Resources

- Next.js Docs: https://nextjs.org/docs  
- React Native Docs: https://reactnative.dev/docs  
- Stripe Docs: https://stripe.com/docs  
- Supabase Docs: https://supabase.com/docs  
- OpenAI API: https://platform.openai.com/docs  

---

⚠️ **Important Notes**  
- Never commit `.env` files  
- Keep dependencies updated (`pnpm update`)  
- Document new modules/features in this file  
- PR reviews required for merges into `main`

