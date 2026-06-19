# Deployment Plan

## Architecture
- **Backend**: Django REST Framework (Travels_App_DjangRF-main/) → Web Service on Render
- **Frontend**: React + Vite (React_Django_travels_project-main/) → Static Site on Render
- **Database**: PostgreSQL (Render provides free tier)

## Steps
1. Fix hardcoded `localhost:8000` URLs in React components to use `API_BASE_URL` from config
2. Add `gunicorn` and `psycopg2-binary` to Django requirements.txt
3. Update Django settings.py for production (ALLOWED_HOSTS, CORS, DATABASES via env)
4. Create Django production build/packaging scripts
5. Push to GitHub
6. Deploy on Render
