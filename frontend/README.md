# LifeLedger Frontend

The web client for **LifeLedger** — an AI-powered personal health intelligence platform and digital health vault.

Built with **Next.js 15 (App Router)**, **React 19**, **TypeScript**, and **Tailwind CSS**.

---

## 🚀 Features

- **Personal Health Dashboard**: Real-time health metrics, records summary, quick actions, and recent activities.
- **AI Health Intelligence**: Upload, extract, and analyze medical reports with automated insights and normal range validations.
- **Digital Health Timeline**: Interactive visual timeline tracking consultations, prescriptions, vaccinations, and lab tests chronologically.
- **Hospital & Emergency Discovery**: Interactive MapLibre & OpenStreetMap facility finder with radius filtering, emergency services, and live booking.
- **Family Health Vault**: Multi-profile management for family dependents with isolated health records and emergency profiles.
- **Secure Medical Sharing**: Time-limited, password/PIN-protected public health record sharing for doctor consultations.
- **Emergency Medical QR**: Instant lock-screen accessible emergency medical cards containing blood group, allergies, medications, and emergency contacts.
- **Comprehensive Profile & Security**: Account security, password updates, dark/light theme toggle, and session management.

---

## 🛠️ Tech Stack

- **Framework**: [Next.js 15](https://nextjs.org/) (App Router, Server & Client Components)
- **Library**: [React 19](https://react.dev/)
- **Language**: [TypeScript](https://www.typescriptlang.org/)
- **Styling**: [Tailwind CSS v4](https://tailwindcss.com/)
- **Component UI**: Radix UI primitives, Lucide Icons, Embla Carousel, Vaul Drawers
- **Maps**: [MapLibre GL](https://maplibre.org/) & OpenStreetMap
- **Data Fetching & State**: [TanStack Query v5](https://tanstack.com/query) & Axios
- **Form Handling & Validation**: React Hook Form & Zod
- **Animations**: Motion (Framer Motion)

---

## 📁 Directory Structure

```
frontend/
├── public/                  # Static assets, maplibre styles, icons
├── scripts/                 # Regression tests & diagnostic utilities
│   ├── copy-maplibre-worker.mjs
│   ├── test_csp_configuration.mjs
│   ├── test_env_resolution.mjs
│   └── test_frontend_contracts.mjs
├── src/
│   ├── app/                 # Next.js App Router (pages & layouts)
│   │   ├── (auth)/          # Sign in, Sign up, Forgot password, Verify OTP
│   │   ├── (dashboard)/     # Main authenticated user dashboard
│   │   ├── (marketing)/     # Landing page, About, Features
│   │   ├── emergency/       # Emergency QR code public access
│   │   ├── medical-share/   # Time-limited shared report viewers
│   │   ├── layout.tsx       # Root layout with providers & theme script
│   │   └── page.tsx         # Root redirect / landing
│   ├── assets/              # Icons and graphics
│   ├── components/          # Reusable UI primitives (buttons, modals, cards)
│   ├── features/            # Feature modules
│   │   ├── family/          # Family vault & dependent management
│   │   ├── health-intelligence/ # AI report analysis
│   │   ├── hospitals/       # Facility locator & map views
│   │   ├── medical-share/   # Secure record sharing
│   │   ├── profile/         # User profile & account security
│   │   ├── reports/         # Medical document uploads & viewing
│   │   ├── settings/        # Preferences & appearance
│   │   └── timeline/        # Health history timeline
│   ├── hooks/               # Custom React hooks (useAuth, useMobile, etc.)
│   ├── lib/                 # Utilities, API client, CSP, env resolution
│   ├── providers/           # QueryClientProvider, ThemeProvider
│   ├── styles.css           # Global stylesheet & design tokens
│   └── types/               # TypeScript interfaces & API schemas
├── .env.example             # Environment template
├── components.json          # UI configuration
├── next.config.ts           # Next.js configuration & CSP headers
├── package.json             # Dependencies and scripts
└── tsconfig.json            # TypeScript configuration
```

---

## ⚙️ Getting Started

### 1. Prerequisites
- Node.js `v20+` or `v22+`
- npm `v10+`

### 2. Environment Setup
Copy the `.env.example` file to `.env.local`:
```bash
cp .env.example .env.local
```

Configure your environment variables:
```env
NEXT_PUBLIC_API_URL=http://localhost:5000/api/v1
NEXT_PUBLIC_APP_URL=http://localhost:3000
```

### 3. Install Dependencies
```bash
npm install
```

### 4. Run Development Server
```bash
npm run dev
```
Open [http://localhost:3000](http://localhost:3000) in your browser.

### 5. Production Build
```bash
npm run build
npm run start
```

---

## 🧪 Tests & Diagnostics

Run frontend configuration and contract diagnostics:
```bash
# Test API URL environment resolution
node scripts/test_env_resolution.mjs

# Test Content Security Policy (CSP) headers
node scripts/test_csp_configuration.mjs

# Test API contracts with backend
node scripts/test_frontend_contracts.mjs
```
