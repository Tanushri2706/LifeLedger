# LifeLedger — AI Health Intelligence Platform & Personal Digital Vault

[![Node.js](https://img.shields.io/badge/Node.js-20+-68A063?logo=node.js&logoColor=white)](https://nodejs.org/)
[![Next.js](https://img.shields.io/badge/Next.js-15-black?logo=next.js&logoColor=white)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=black)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.8-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-v4-06B6D4?logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)
[![Express.js](https://img.shields.io/badge/Express.js-4.21-000000?logo=express&logoColor=white)](https://expressjs.com/)
[![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-47A248?logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![Google Gemini](https://img.shields.io/badge/Google_Gemini-2.0-8E75C2?logo=google&logoColor=white)](https://ai.google.dev/)

**LifeLedger** is a production-grade, AI-powered healthcare ecosystem designed to securely store, organize, and transform fragmented medical documents into actionable personal health intelligence.

---

## 🌟 Core Modules

1. **Personal Health Dashboard**: Centralized view of vitals, upcoming doctor appointments, recent reports, and wellness metrics.
2. **AI Health Intelligence**: Upload lab reports (PDF/images); Google Gemini extracts parameters, evaluates reference ranges, flags abnormal values, and produces clinician-level plain-language summaries.
3. **Digital Health Vault**: Secure medical report storage with Cloudinary, categorized by type (Lab Tests, Prescriptions, Scans, Discharge Summaries).
4. **Chronological Health Timeline**: Visual journey mapping medical events, diagnoses, treatments, and vaccinations over time.
5. **Nearby Hospitals & Doctors**: Interactive map with OpenStreetMap & MapLibre GL to discover facilities, view emergency ER readiness, and book appointments.
6. **Family Health Management**: Multi-profile vault supporting children and elderly family members with isolated medical records.
7. **Emergency Health Profile & QR**: Instant lock-screen scan QR code exposing critical lifesaving medical data (blood group, allergies, medications, emergency contacts) without login.
8. **Secure Time-Limited Medical Sharing**: Generate PIN-protected, expiration-controlled share links for doctors and specialists.

---

## 🏗️ System Architecture

```
                                  +-----------------------------+
                                  |      LifeLedger Client      |
                                  |   (Next.js 15 + React 19)   |
                                  +--------------+--------------+
                                                 |
                                         REST API Calls
                                                 |
                                                 v
                                  +-----------------------------+
                                  |    LifeLedger Backend API   |
                                  |    (Express + TypeScript)   |
                                  +----+----+---------------+---+
                                       |    |               |
               +-----------------------+    |               +-----------------------+
               |                            |                                       |
               v                            v                                       v
     +-------------------+        +-------------------+                   +-------------------+
     |   MongoDB Atlas   |        |  Google Gemini AI |                   | Cloudinary / Brevo|
     | (Database Store)  |        | (OCR & Extraction)|                   | (Storage & Email) |
     +-------------------+        +-------------------+                   +-------------------+
```

---

## 📁 Repository Structure

```
LifeLedger/
├── backend/                  # Node.js + Express + TypeScript + MongoDB REST API
│   ├── src/
│   │   ├── config/           # Environment validation & DNS configuration
│   │   ├── controllers/      # REST API request handlers
│   │   ├── middleware/       # Auth, rate limiting, error handling, upload
│   │   ├── models/           # Mongoose schemas & data models
│   │   ├── routes/           # Versioned Express routes (/api/v1)
│   │   ├── services/         # Core business logic (AI, email, storage)
│   │   ├── types/            # TypeScript data contracts & DTOs
│   │   ├── utils/            # Token generation, hashing, standard responses
│   │   ├── __tests__/        # Unit test suites (JWT, rate limiter, radius)
│   │   ├── app.ts            # Express application setup
│   │   └── server.ts         # Server bootstrapper & database connection
│   ├── .env.example          # Backend environment template
│   ├── package.json          # Backend dependencies & scripts
│   ├── tsconfig.json         # Backend TypeScript configuration
│   └── README.md             # Backend detailed documentation
│
├── frontend/                 # Next.js 15 + React 19 + Tailwind CSS Web App
│   ├── public/               # Static assets & maplibre worker
│   ├── scripts/              # Frontend diagnostic & test scripts
│   ├── src/
│   │   ├── app/              # App router pages (auth, dashboard, marketing)
│   │   ├── components/       # Reusable UI component library (Radix UI)
│   │   ├── features/         # Domain feature slices (vault, map, AI, profile)
│   │   ├── hooks/            # Custom React hooks (auth, mobile, state)
│   │   ├── lib/              # API clients, CSP configurations, helpers
│   │   ├── providers/        # React Query and Theme providers
│   │   ├── styles.css        # Global CSS & Tailwind theme tokens
│   │   └── types/            # Frontend TypeScript type declarations
│   ├── .env.example          # Frontend environment template
│   ├── next.config.ts        # Next.js build configuration & CSP headers
│   ├── package.json          # Frontend dependencies & scripts
│   ├── tsconfig.json         # Frontend TypeScript configuration
│   └── README.md             # Frontend detailed documentation
│
├── docs/                     # Full Technical Architecture & Specifications
│   ├── API.md                # Comprehensive REST API specifications
│   ├── ARCHITECTURE.md       # High-level architecture and subsystem designs
│   ├── CHANGELOG.md          # Release logs and version history
│   ├── DATABASE.md           # MongoDB schemas, indexing, and ER designs
│   ├── DESIGN.md             # Design principles, typography, and color palettes
│   ├── MEMORY.md             # Architectural decisions and project context
│   ├── PHASES.md             # Development roadmap and sprint breakdown
│   ├── PRD.md                # Product Requirements Document
│   ├── PROJECT_STATUS.md     # Current milestone and delivery status
│   ├── SECURITY.md           # Threat modeling and security controls
│   └── TECH_SPEC.md          # Detailed technical specification
│
├── .gitignore                # Production root gitignore (ignores secrets, logs, node_modules)
└── README.md                 # Master project documentation
```

---

## ⚡ Quick Start Guide

Follow these steps to run the complete LifeLedger full-stack platform locally.

### 1. Prerequisites
- [Node.js](https://nodejs.org/) v20+ or v22+
- [Git](https://git-scm.com/)
- [MongoDB](https://www.mongodb.com/) running locally or a MongoDB Atlas URI

### 2. Clone the Repository
```bash
git clone https://github.com/Tanushri2706/LifeLedger.git
cd LifeLedger
```

### 3. Setup and Start Backend
```bash
cd backend

# Create .env from example template
cp .env.example .env

# Install dependencies
npm install

# Start backend development server (runs at http://localhost:5000)
npm run dev
```

### 4. Setup and Start Frontend
In a new terminal:
```bash
cd frontend

# Create .env.local from example template
cp .env.example .env.local

# Install dependencies
npm install

# Start frontend development server (runs at http://localhost:3000)
npm run dev
```

Visit **[http://localhost:3000](http://localhost:3000)** in your browser!

---

## 🔐 Environment Configuration

### Backend (`backend/.env.example`)
| Variable | Description | Default / Example |
| :--- | :--- | :--- |
| `PORT` | Backend server port | `5000` |
| `NODE_ENV` | Runtime environment | `development` |
| `CLIENT_URL` | Allowed origin for CORS | `http://localhost:3000` |
| `MONGODB_URI` | MongoDB connection string | `mongodb://localhost:27017/lifeledger` |
| `JWT_ACCESS_SECRET` | Secret key for access JWTs | Min 32 characters |
| `JWT_REFRESH_SECRET` | Secret key for refresh JWTs | Min 32 characters |
| `GEMINI_API_KEY` | Google Gemini AI API Key | API key from Google AI Studio |
| `CLOUDINARY_*` | Cloudinary storage credentials | Cloud name, API key & secret |
| `BREVO_API_KEY` | Brevo email provider API Key | (Optional in dev, mock fallback used) |

### Frontend (`frontend/.env.example`)
| Variable | Description | Default / Example |
| :--- | :--- | :--- |
| `NEXT_PUBLIC_API_URL` | Base URL of the LifeLedger Backend API | `http://localhost:5000/api/v1` |
| `NEXT_PUBLIC_APP_URL` | Frontend canonical URL for OpenGraph & URLs | `http://localhost:3000` |

---

## 📡 API Overview (v1)

The backend provides a standardized REST API rooted at `/api/v1`:

| Module | Endpoint | Method | Description |
| :--- | :--- | :--- | :--- |
| **Health** | `/health` | `GET` | Service health status check |
| **Auth** | `/auth/register` | `POST` | Register a new user |
| **Auth** | `/auth/login` | `POST` | Authenticate user & issue tokens |
| **Auth** | `/auth/refresh` | `POST` | Refresh expired access token |
| **Auth** | `/auth/logout` | `POST` | Invalidate refresh token & clear cookies |
| **User** | `/users/me` | `GET` | Get current user profile |
| **Reports** | `/reports/upload` | `POST` | Upload medical report (PDF / Image) |
| **AI** | `/ai/analyze/:id` | `POST` | Trigger AI analysis on a report |
| **Timeline** | `/timeline` | `GET` | Get chronological medical events |
| **Hospitals** | `/hospitals/nearby` | `GET` | Find nearby hospitals by latitude/longitude |
| **Family** | `/family` | `GET` | Get family dependent profiles |
| **Emergency** | `/emergency/:id` | `GET` | Public emergency profile by QR token |
| **Share** | `/medical-share` | `POST` | Create a time-limited medical share link |

For complete documentation on schemas and payloads, consult [docs/API.md](docs/API.md).

---

## 🛡️ Medical & Legal Disclaimer

LifeLedger's AI-assisted features are designed exclusively to help users comprehend and organize their healthcare records. AI-generated insights, ranges, and summaries are **not medical diagnoses** and should never substitute professional medical advice, clinical evaluations, or emergency care from licensed healthcare providers.

---

## 👩‍💻 Author & Contributions

Created and maintained by [Tanushri](https://github.com/Tanushri2706).
Feel free to open issues or submit pull requests to contribute!
