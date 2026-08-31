# AI Resume Builder & Optimizer

An AI-powered app that analyzes your resume against a target job description and generates a personalized interview preparation report — technical questions, behavioral questions, skill gaps, a preparation plan, and an optimized, downloadable resume PDF.

## Features

- 🔐 User authentication (register/login) with JWT stored in an HTTP-only cookie
- 📄 Upload a resume (PDF) and/or a quick self-description, plus a target job description
- 🤖 AI-generated interview report (technical & behavioral questions, skill gaps, preparation plan, match score) via Google GenAI
- 📥 Download an AI-optimized resume as a PDF, tailored to the job description
- 🗂️ View your history of previously generated interview reports

## Tech Stack

**Backend**
- Node.js, Express 5
- MongoDB with Mongoose
- Google GenAI (`@google/genai`) for report/resume generation
- Puppeteer for server-side PDF generation
- JWT (`jsonwebtoken`) + `bcryptjs` for authentication
- `multer` for resume file uploads, `pdf-parse` for extracting resume text

**Frontend**
- React 19 + Vite
- React Router
- Axios
- SCSS

## Project Structure

```
Backend/     Express API, MongoDB models, auth, AI report/resume generation
Frontend/    React + Vite single-page app
```

## Getting Started

### Prerequisites
- Node.js
- A MongoDB connection string (local or [MongoDB Atlas](https://www.mongodb.com/cloud/atlas/register))
- A Google GenAI API key ([Google AI Studio](https://aistudio.google.com/apikey))

### Backend setup

```bash
cd Backend
npm install
```

Create a `.env` file in `Backend/` with:

```
MONGO_URI=<your MongoDB connection string>
JWT_SECRET=<any random secret string>
GOOGLE_GENAI_API_KEY=<your Google GenAI API key>
```

Run the server:

```bash
npm run dev
```

The API runs on `http://localhost:3000`.

### Frontend setup

```bash
cd Frontend
npm install
npm run dev
```

The app runs on `http://localhost:5173`.

## API Overview

| Method | Route | Description |
|---|---|---|
| POST | `/api/auth/register` | Register a new user |
| POST | `/api/auth/login` | Log in a user |
| GET | `/api/auth/logout` | Log out the current user |
| GET | `/api/auth/get-me` | Get the logged-in user's details |
| POST | `/api/interview/` | Generate an interview report from resume + job description |
| GET | `/api/interview/` | List the logged-in user's interview reports |
| GET | `/api/interview/report/:interviewId` | Get a single interview report |
| POST | `/api/interview/resume/pdf/:interviewReportId` | Generate & download an optimized resume PDF |
