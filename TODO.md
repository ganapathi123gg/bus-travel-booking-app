# TODO - BUS TRAVEL APP DEPLOYMENT

## Completed Code Setup
- [x] Read all project files (React frontend + Django backend)
- [x] Fixed hardcoded `localhost:8000` URLs in LoginForm.jsx → uses `API_BASE_URL` from config
- [x] Fixed hardcoded `localhost:8000` URLs in RegisterForm.jsx → uses `API_BASE_URL` from config
- [x] Updated Django settings.py for production:
  - [x] SECRET_KEY via env variable
  - [x] DEBUG via env variable
  - [x] ALLOWED_HOSTS via env variable
  - [x] CORS_ALLOWED_ORIGINS via env variable
  - [x] PostgreSQL via DATABASE_URL env variable
  - [x] Added whitenoise middleware for static files
  - [x] Added STATIC_ROOT and STATICFILES_STORAGE config
- [x] Updated requirements.txt with production deps (gunicorn, psycopg2-binary, dj-database-url, whitenoise)
- [x] Created build.sh (migrations + collectstatic + superuser)
- [x] Created Procfile (gunicorn)
- [x] Created render.yaml (Render Blueprint: Django API + React static + PostgreSQL)
- [x] Updated vite.config.js with production build settings

## Deployment Steps (to complete on Render)
- [ ] Push all changes to GitHub
  ```
  git add .
  git commit -m "Deployment prep: env config, render blueprint, production settings"
  git push origin main
  ```
- [ ] Go to https://dashboard.render.com
- [ ] Click "New +" → "Blueprint" → connect your GitHub repo
- [ ] Select `bus-travel-booking-app` repo
- [ ] Render reads `render.yaml` → creates 3 resources automatically:
  1. **ganapathi-travels-db** (PostgreSQL)
  2. **ganapathi-travels-api** (Django web service)
  3. **ganapathi-travels** (React static site)
- [ ] Wait for deploy (~5 min for first deploy)
- [ ] Visit: https://ganapathi-travels.onrender.com

## Post-Deployment
- [ ] Create a superuser: Run in Render shell → `python travels/manage.py createsuperuser`
- [ ] Add bus data via Django admin or seed script
- [ ] Verify /api/buses/ returns data
- [ ] Verify frontend loads and can call backend API
