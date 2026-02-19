# Cookiecutter Django + React

A production-ready cookiecutter template for Django + React applications with:

- **Backend**: Django + Django REST Framework + django-allauth (Google OAuth)
- **Frontend**: React 19 + TypeScript + Vite + Tailwind CSS v4
- **Auth**: Google OAuth via django-allauth, session-based auth, CSRF protection
- **Deployment**: Docker + Nginx reverse proxy, Railway-ready env files
- **CI/CD**: GitHub Actions (lint, test, build)
- **Features**: Dark/light/system theme, PWA support, responsive design

## Quick Start

```bash
# Install cookiecutter
pip install cookiecutter

# Generate your project
cookiecutter path/to/cookiecutter-django-react

# Follow the prompts for project_name, author, etc.
```

## What You Get

```
your_project/
├── backend/          # Django + DRF + allauth
├── frontend/         # React + TypeScript + Vite + Tailwind
├── docker-compose.yml
├── docker-compose.prod.yml
└── .github/workflows/ci.yml
```

## Development

After generating your project:

```bash
# Backend
cd your_project/backend
uv venv && source .venv/bin/activate
uv sync
python manage.py migrate
python manage.py runserver

# Frontend (in another terminal)
cd your_project/frontend
npm install
npm run dev
```

## Railway Deployment

Railway env templates are included:
- `backend/.env.backend.railway` - Backend service variables
- `frontend/.env.frontend.railway` - Frontend service variables

Set these in your Railway dashboard. See the generated project's README for details.

## Google OAuth Setup

1. Go to [Google Cloud Console](https://console.cloud.google.com/apis/credentials)
2. Create an OAuth 2.0 Client ID
3. Set authorized redirect URI to `http://localhost:8000/accounts/google/login/callback/` (dev) or your production URL
4. Add `GOOGLE_CLIENT_ID` and `GOOGLE_CLIENT_SECRET` to your `.env`
5. Run migrations and create a SocialApp in Django admin, or configure via settings
