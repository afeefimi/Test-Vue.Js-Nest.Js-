# Test-Vue.Js-Nest.Js-

A monorepo containing a Vue.js frontend and a NestJS backend.

## Tech Stack

- **Frontend:** Vue.js 3 (Vite, Vue Router, Pinia, Vitest, ESLint, Prettier)
- **Backend:** NestJS (TypeScript)

## Project Structure

```
.
├── frontend/     # Vue.js application
├── backend/      # NestJS application
└── README.md
```

## Prerequisites

- Node.js (LTS recommended)
- npm
- Git (with SSH access configured for this repository)

## Setup Instructions

### 1. Clone the repository

```bash
git clone git@github.com:<your-username>/<repo-name>.git
cd <repo-name>
```

### 2. Install frontend dependencies

```bash
cd frontend
npm install
```

### 3. Install backend dependencies

```bash
cd ../backend
npm install
```

### 4. Configure environment variables

Copy the example env files and fill in your local values:

```bash
# from the frontend/ folder
cp .env.example .env

# from the backend/ folder
cp .env.example .env
```

Fill in the actual values in each `.env` file (see `.env.example` in each folder for the required keys). Credentials should be retrieved from your team's password manager (e.g. Bitwarden) — never commit real `.env` files or credentials to the repository.

### 5. Run the applications locally

**Backend** (from `backend/`):

```bash
npm run start:dev
```

Runs by default on `http://localhost:3000`.

**Frontend** (from `frontend/`):

```bash
npm run dev
```

Runs by default on `http://localhost:5173`.

Open the frontend URL in your browser and confirm it can successfully reach the backend (check the browser Network tab for any errors).

## Branch Strategy

This repository follows a Feature Branch → Staging → Production flow:

```
main       ← Production
staging    ← Staging / QA environment
feature/*  ← Individual feature branches
```

**Workflow:**

1. Create a feature branch off `staging`:
   ```bash
   git checkout staging
   git pull
   git checkout -b feature/short-description
   ```
2. Commit your work and push the branch:
   ```bash
   git push -u origin feature/short-description
   ```
3. Open a Pull Request / Merge Request into `staging`.
4. After review and approval, merge and delete the feature branch.
5. Once `staging` is verified stable, open a Pull Request / Merge Request from `staging` into `main` to release to production.

`main` and `staging` are protected branches: direct pushes are disabled, and all changes must go through a reviewed Pull Request / Merge Request.

## Available Scripts

### Frontend (`frontend/`)

| Command | Description |
|---|---|
| `npm run dev` | Start local dev server |
| `npm run build` | Type-check and build for production |
| `npm run test:unit` | Run unit tests (Vitest) |
| `npm run lint` | Lint and auto-fix |
| `npm run format` | Format code with Prettier |

### Backend (`backend/`)

| Command | Description |
|---|---|
| `npm run start:dev` | Start local dev server (watch mode) |
| `npm run build` | Build for production |
| `npm run test` | Run unit tests |
| `npm run test:e2e` | Run end-to-end tests |
| `npm run lint` | Lint and auto-fix |