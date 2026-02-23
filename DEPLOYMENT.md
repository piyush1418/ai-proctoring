# Deployment Guide - AI-Based Online Exam Proctoring System

## Render Deployment Steps

### 1. Create GitHub Repository
- Go to https://github.com/new
- Repository name: `exam-proctoring-system`
- Description: AI-Based Online Exam Proctoring System
- Make it **Public**
- Click "Create repository"

### 2. Upload Files to GitHub (Web UI Method)
- On your new GitHub repo, click "Add file" → "Upload files"
- Upload the entire `futurproctor` folder
- Add a commit message: "Initial commit"
- Click "Commit changes"

### 3. Create Render Web Service
- Go to https://render.com
- Sign up with GitHub
- Click "New +" → "Web Service"
- Select your `exam-proctoring-system` repository
- Configure:
  - **Name**: exam-proctoring
  - **Environment**: Python 3
  - **Build Command**: `pip install -r requirements.txt && python manage.py collectstatic --no-input && python manage.py migrate --skip-checks`
  - **Start Command**: `gunicorn futurproctor.wsgi:application`
  - **Plan**: Free

### 4. Set Environment Variables in Render
- Go to Service Settings → Environment
- Add these variables:

| Key | Value |
|-----|-------|
| SECRET_KEY | `your-super-secret-key-12345` |
| DEBUG | `False` |
| ALLOWED_HOSTS | `your-app-name.onrender.com` |
| DATABASE_URL | Leave empty for now (SQLite will be used) |

### 5. Deploy
- Click "Create Web Service"
- Monitor the build in the "Logs" tab
- Once build succeeds, get your live URL!

## Local Development

### Run Locally
```bash
cd futurproctor
python manage.py runserver
```

Access at: http://localhost:8000

### Create Admin User
```bash
python manage.py createsuperuser
```

## Support
For issues, check Render logs or Django logs.
