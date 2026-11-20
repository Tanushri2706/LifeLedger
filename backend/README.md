# LifeLedger Backend API

REST API server powering the **LifeLedger Health Intelligence Platform**.

Built with **Node.js**, **Express.js**, **TypeScript**, **MongoDB (Mongoose)**, and **Google Gemini AI**.

---

## 🚀 Features

- **Authentication & Security**:
  - JWT Access & Refresh Token rotation with HttpOnly cookies.
  - Role-based Access Control (Patient, Doctor, Admin).
  - Rate limiting (Express Rate Limit) and security headers (Helmet).
  - Password hashing with Bcrypt (configurable salt rounds).
  - OTP verification for sign-up, password reset, and sensitive profile actions.
- **AI Health Intelligence**:
  - Medical report PDF and image processing with Google Gemini 2.0.
  - Automated lab parameter extraction with reference ranges and abnormal flag detection.
  - Document OCR and structured clinical summary extraction.
- **Health Vault & Records Management**:
  - Secure medical report storage integrated with Cloudinary.
  - Chronological health timeline event tracking.
  - Family dependent profile isolation and shared health history.
- **Facility Discovery & Emergency**:
  - Geospatial queries for nearby hospitals and clinics (OSM / Google Maps providers).
  - Emergency QR code generation with instantaneous public data endpoint.
  - Time-limited medical sharing links with PIN protection.
- **Email Notifications**:
  - Brevo (Sendinblue) transactional email provider integration with automatic mock fallback for development.

---

## 🛠️ Tech Stack

- **Runtime**: [Node.js](https://nodejs.org/) (ES2022)
- **Framework**: [Express.js v4](https://expressjs.com/)
- **Language**: [TypeScript v5](https://www.typescriptlang.org/)
- **Database**: [MongoDB](https://www.mongodb.com/) via [Mongoose v8](https://mongoosejs.com/)
- **AI Integration**: [@google/genai](https://www.npmjs.com/package/@google/genai)
- **File Upload & Storage**: Multer & Cloudinary
- **Validation**: Zod
- **Development Tooling**: `tsx` (TypeScript Execute & Watch)

---

## 📁 Directory Structure

```
backend/
├── src/
│   ├── config/              # Environment config validation & DNS failover
│   ├── controllers/         # Request handlers
│   │   ├── ai.controller.ts
│   │   ├── appointment.controller.ts
│   │   ├── auth.controller.ts
│   │   ├── dashboard.controller.ts
│   │   ├── doctor.controller.ts
│   │   ├── emergency.controller.ts
│   │   ├── family.controller.ts
│   │   ├── health.controller.ts
│   │   ├── hospital.controller.ts
│   │   ├── medicalReport.controller.ts
│   │   ├── medicalShare.controller.ts
│   │   ├── timeline.controller.ts
│   │   └── user.controller.ts
│   ├── middleware/          # Auth, RateLimiter, Upload, ErrorHandler, Logger
│   ├── models/              # Mongoose schemas & data models
│   ├── routes/              # Express route registrations (v1)
│   ├── services/            # Business logic (AI analysis, email, storage, etc.)
│   ├── types/               # TypeScript interfaces & DTOs
│   ├── utils/               # Token helpers, password hashing, standard responses
│   ├── __tests__/           # Unit tests (JWT, rate limiter, radius queries)
│   ├── app.ts               # Express application setup & middleware stack
│   └── server.ts            # Server entry point & DB connection lifecycle
├── .env.example             # Environment variable template
├── .gitignore               # Backend gitignore
├── package.json             # Dependencies and scripts
└── tsconfig.json            # TypeScript compiler configuration
```

---

## ⚙️ Getting Started

### 1. Prerequisites
- Node.js `v20+` or `v22+`
- Local MongoDB or MongoDB Atlas URI

### 2. Environment Setup
Copy `.env.example` to `.env`:
```bash
cp .env.example .env
```

Key environment variables:
```env
PORT=5000
NODE_ENV=development
CLIENT_URL=http://localhost:3000
MONGODB_URI=mongodb://localhost:27017/lifeledger
JWT_ACCESS_SECRET=your_jwt_access_secret_key_minimum_32_characters_here
JWT_REFRESH_SECRET=your_jwt_refresh_secret_key_minimum_32_characters_here
CLOUDINARY_CLOUD_NAME=your_cloudinary_name
CLOUDINARY_API_KEY=your_cloudinary_key
CLOUDINARY_API_SECRET=your_cloudinary_secret
GEMINI_API_KEY=your_gemini_api_key
BREVO_API_KEY=your_brevo_api_key
```

### 3. Install Dependencies
```bash
npm install
```

### 4. Run Development Server
```bash
npm run dev
```
The server will start at [http://localhost:5000](http://localhost:5000) with health check at `/api/v1/health`.

### 5. Typecheck & Build
```bash
# Typecheck without emitting
npm run typecheck

# Build JavaScript for production
npm run build

# Start production server
npm start
```
