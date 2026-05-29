<div align="center">

<img src="https://img.shields.io/badge/FoLiOAi-Seller%20Finance%20Intelligence-7F77DD?style=for-the-badge&logoColor=white" alt="FoLiOAi" />

<br/>
<br/>

**AI-powered Amazon India seller reconciliation.**
Deterministic leakage detection · GST audit · TCS recovery · Gemini AI narratives

<br/>

[![Live Demo](https://img.shields.io/badge/Live%20Demo-folioai--production.up.railway.app-1D9E75?style=flat-square&logo=railway&logoColor=white)](https://folioai-production.up.railway.app/)
[![TypeScript](https://img.shields.io/badge/TypeScript-95%25-3178C6?style=flat-square&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![React](https://img.shields.io/badge/React-Vite-61DAFB?style=flat-square&logo=react&logoColor=black)](https://vitejs.dev/)
[![Firebase](https://img.shields.io/badge/Firebase-Auth%20%2B%20Firestore-FFCA28?style=flat-square&logo=firebase&logoColor=black)](https://firebase.google.com/)
[![Gemini](https://img.shields.io/badge/Google-Gemini%20AI-4285F4?style=flat-square&logo=google&logoColor=white)](https://aistudio.google.com/)
[![Railway](https://img.shields.io/badge/Deployed%20on-Railway-0B0D0E?style=flat-square&logo=railway&logoColor=white)](https://railway.app/)

</div>

---

## What is FoLiOAi?

Amazon India sellers lose thousands of rupees every month to undetected leakage — short payments, GST mismatches, and TCS discrepancies buried in dense settlement CSVs. FoLiOAi solves this.

Upload your settlement report and get an instant, auditable breakdown of where your money went — and how much is recoverable.

> **Core design rule:** AI never computes. Every ₹ figure is produced by deterministic TypeScript functions. Gemini only writes the plain-language narrative around numbers it didn't touch.

---

## Features

| Feature | Description |
|---|---|
| Revenue & profit breakdown | Per-SKU and per-month P&L from raw settlement data |
| Leakage detection | 5 leakage types flagged with exact source row references |
| GST / TCS / TDS reconciliation | Mismatch table with full audit trail |
| AI narrative | Gemini-powered plain-language financial summary |
| Confidence scoring | High / Medium / Low data quality score on every report |
| DPDP Act 2023 compliance | Consent modal gates every file upload |
| Paywall pattern | Teaser shows recoverable amount, detail locked behind Growth plan |

---

## Tech Stack

```
Frontend    React 18 + TypeScript + Vite
Backend     Express + BullMQ (job queue)
AI          Google Gemini API
Auth & DB   Firebase Authentication + Firestore
Deployment  Railway (production) · In-memory Redis mock (dev)
```

---

## Project Structure

```
folio-ai/
├── server.ts                         ← Express backend · BullMQ jobs · AI chat API
├── src/
│   ├── App.tsx                       ← Main router + auth gate
│   ├── types/index.ts                ← All TypeScript types
│   ├── lib/
│   │   ├── queue.ts                  ← BullMQ queue + worker
│   │   ├── firebase.ts               ← Firebase client
│   │   ├── reconcile/
│   │   │   ├── parser.ts             ← CSV ingestion + column mapping
│   │   │   ├── leakage.ts            ← Deterministic leakage detection (5 types)
│   │   │   ├── gst.ts                ← GST + TCS reconciliation
│   │   │   ├── settlement.ts         ← Totals · SKU profitability · monthly trends
│   │   │   └── confidence.ts         ← Data quality scoring
│   │   └── ai/
│   │       └── narrative.ts          ← Gemini narrative layer
│   ├── pages/
│   │   ├── Upload.tsx
│   │   └── Dashboard.tsx
│   └── components/
│       ├── auth/
│       │   ├── LoginPage.tsx
│       │   └── ConsentModal.tsx      ← DPDP Act 2023 compliance
│       ├── dashboard/
│       │   ├── MetricCards.tsx
│       │   ├── LeakageBreakdown.tsx
│       │   ├── GstMismatchTable.tsx
│       │   ├── SkuProfitability.tsx
│       │   ├── MonthlyTrends.tsx
│       │   └── PaywallOverlay.tsx
│       ├── chat/
│       │   └── AiChatPanel.tsx
│       └── shared/
│           └── Navbar.tsx
├── firestore.rules
├── Dockerfile
├── docker-compose.yml
├── vite.config.ts
└── tsconfig.json
```

---

## Getting Started

### Prerequisites

- Node.js 18+
- A [Gemini API key](https://aistudio.google.com/app/apikey) (free)
- A [Firebase project](https://console.firebase.google.com/) with Auth + Firestore enabled

### 1. Clone & install

```bash
git clone https://github.com/sajid-mohd/FoLiO.ai.git
cd FoLiO.ai
npm install
```

### 2. Configure environment

Create `.env.local`:

```env
GEMINI_API_KEY="your_gemini_key"
APP_URL="http://localhost:3000"

# Production only
# REDIS_URL="redis://your-redis-url"
```

> No Redis needed in dev — the app uses an in-memory mock automatically.

### 3. Run

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000)

---

## Firebase Setup

1. Go to [Firebase Console](https://console.firebase.google.com)
2. Create a project → enable **Authentication** (Google provider) and **Firestore**
3. Add a Web app and copy the config
4. Replace values in `src/lib/firebase.ts`
5. Deploy rules:

```bash
firebase deploy --only firestore:rules
```

To unlock Growth plan features in dev, set the `plan` field to `"growth"` on your Firestore user document.

---

## Docker

```bash
docker-compose up --build
```

---

## Design Principles

1. **Deterministic first** — all financial figures come from pure TypeScript functions, never from AI inference
2. **Audit trail** — every leakage item carries `sourceRows[]` pointing back to the original CSV
3. **Trust by default** — confidence score on every report so sellers know how reliable the data is
4. **Privacy compliant** — DPDP Act 2023 consent modal before any data leaves the browser
5. **Honest monetisation** — teaser shows real recoverable amount; paywall locks the breakdown, not the insight

---

## Legal

- All figures are informational only and do not constitute CA or tax advice
- DPDP Act 2023 consent obtained before every file upload
- Data stored on Google Cloud infrastructure via Firebase

---

<div align="center">

Built by [Mohammad Sajid](https://www.linkedin.com/in/mohammadsajid2) · Bengaluru, India

</div>
