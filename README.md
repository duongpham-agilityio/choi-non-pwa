<div align="center">

# 🌱 Chồi Non

**Supporting mothers through every stage of pregnancy and early motherhood, together.**

A PWA for pregnant women and mothers of babies aged 0–12 months: a stage-based community feed, a sourced knowledge library, and an AI assistant that answers only from reviewed articles.

![Status](https://img.shields.io/badge/status-v0-F5C842)
![Platform](https://img.shields.io/badge/platform-PWA-0A8444)
![Next.js](https://img.shields.io/badge/Next.js-16-000)
![Monorepo](https://img.shields.io/badge/Turborepo-pnpm-22B866)

</div>

---

## Table of contents

- [Why Chồi Non](#why-chồi-non)
- [MVP features](#mvp-features)
- [Out of scope for the first version](#out-of-scope-for-the-first-version)
- [Product principles](#product-principles)
- [Design](#design)
- [Tech stack and repo structure](#tech-stack-and-repo-structure)
- [Getting started](#getting-started)
- [Disclaimer](#disclaimer)

---

## Why Chồi Non

Information about pregnancy and caring for a young baby is overwhelming, often contradictory, and mothers don't know whom to trust. Chồi Non exists to solve exactly that for the people close to the author. It is not a startup or a portfolio piece.

- **Core pain point:** too much information, conflicting, hard to trust.
- **Success after 6–12 months:** a group of mothers using the app every week.
- **How it's measured:** weekly active mothers, plus short interviews with 5–10 people.
- **First testers:** 5–10 friends and family.
- **Resources:** side project, a few hours per week, self-funded during the trial.

### Audience and stages

The mother's or baby's stage is the organizing axis of the whole app. It drives the Feed, the Knowledge articles and the AI's context. Users can still browse other stages.

| Stage | Code | Applies to |
| --- | --- | --- |
| Pregnancy | `preg` | Expecting mothers |
| Newborn | `newborn` | Baby 0–3 months |
| Infant | `infant` | Baby 4–6 months |
| Baby | `baby` | Baby 7–12 months |

---

## MVP features

Three equal tabs: **Feed**, **Knowledge** (Kiến thức), **Ask AI** (Hỏi AI).

### 1. Feed: a compact community

- Open the app and see ready-made posts alongside posts from other mothers, like a condensed Facebook.
- Filter by stage, like, save, comment and reply.
- **Mother-and-baby topics only.** It is not a general-purpose social network.
- Pre-written editorial posts (marked **Reviewed** with a source) so the Feed is never empty at the start.
- Moderation: AI scans posts and flags incorrect medical content and advertising. A report button is available.

### 2. Knowledge: an editorial library

- Article-style pieces with images, filterable by stage and searchable.
- Rewritten in Chồi Non's own words from several trusted sources (Ministry of Health, WHO, National Institute of Nutrition), **with the source and original link credited**. Nothing is copied verbatim.
- Copyright-free images (Unsplash, Pexels) or original illustrations.
- Every article shows: source, last-updated date, applicable stage, and a "reference information" label.
- Start with roughly **15–30 articles** covering the most common questions rather than broad coverage.

### 3. Ask AI: the assistant "Nụ"

- **Answers only from the reviewed article library** and links back to the source article. One library serves both reading and Q&A, and the AI never invents content outside it.
- Topics in the first version:
  - Nutrition during pregnancy (what to eat and avoid)
  - Postpartum nutrition and breastfeeding
  - Newborn care, 0–3 months
  - Weaning and babies aged 4–12 months
- **Safety:** for warning signs (abdominal pain, bleeding, high fever in a baby, and so on) the AI does not diagnose. It advises seeing a doctor right away and lists the emergency signs.
- It clearly separates reference information from personal medical advice and does not replace a doctor or dietitian.

### 4. Accounts and personalization

- Sign in with an **email magic link** or **Google**, collecting minimal data.
- Three-step onboarding: what to call the mother, her stage (pregnancy week or baby's date of birth), and stage-based reminders. The stage updates automatically over time.

### 5. Coming back

- Stage-based notifications and reminders: one short tip per week, no ads.
- At first, the project owner messages testers directly.

---

## Out of scope for the first version

- Baby Memories (private photos, notes, milestones): after Feed and AI work well.
- Private chat between mothers, discussion groups.
- Expert system and verified consultations.
- Native app, Zalo/Messenger bot, business registration.
- Revenue and business model.

---

## Product principles

1. **Stay on topic:** mother-and-baby subjects only.
2. **Trust first:** medical content must be sourced; the AI never invents beyond the library.
3. **Privacy:** pregnancy and baby data is sensitive, so collect the minimum. Consider Vietnam's personal-data protection rules before opening up beyond people we know.
4. **Clean copyright:** no copying of articles or images from elsewhere.
5. **Small enough to ship:** scope must fit a few hours per week.

---

## Design

The v0 design lives on Claude Design: **[Chồi Non · v0](https://claude.ai/artifact/SPj5Y443hD1SsacmK8Q5tq)**. It has 10 artboards:

| Group | Artboards |
| --- | --- |
| Screens (390×844) | Sign in · First-time onboarding · Feed · Comments · Knowledge · Ask AI |
| Foundations | Proposed palettes · Palette & Foundations · Components · Logo |

The design is the source of truth for the UI. When implementing, bring its tokens into the Tailwind theme so every screen shares them.

---

## Tech stack and repo structure

A **Turborepo + pnpm workspaces** monorepo.

| Layer | Choice |
| --- | --- |
| Web | Next.js 16 (App Router), React 19, TypeScript |
| Styling | Tailwind CSS 4 |
| Lint / types | ESLint 9, `tsc --noEmit` |
| Build | Turborepo, pnpm 10 |

```
choi-non/
├── apps/
│   ├── web/        Next.js PWA (@choi-non/web)
│   └── mobile/     Expo app (TODO, not installed yet)
├── packages/       shared code (empty)
├── turbo.json
└── pnpm-workspace.yaml
```

---

## Getting started

**Requirements:** Node.js 20+, pnpm 10 (`corepack enable` is enough).

```bash
pnpm install
pnpm dev          # run all apps
```

Run the web app only:

```bash
pnpm --filter @choi-non/web dev
```

Other commands:

```bash
pnpm build        # build everything
pnpm lint
pnpm typecheck
```

---

## Disclaimer

Chồi Non provides **reference information only**. It does not replace a doctor, a dietitian or personal medical advice. If anything seems wrong, see a doctor or call emergency services (**115** in Vietnam).
