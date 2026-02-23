# AI Proctoring System - Deployment Guide

## Quick Deploy Options

### Option 1: Railway (Easiest - 5 minutes)
1. Go to https://railway.app
2. Sign in with GitHub
3. Click "New Project" → "Deploy from GitHub repo"
4. Select: piyush1418/ai-proctoring
5. Railway auto-detects Django and deploys
6. Get public URL instantly

### Option 2: Render (Free)
1. Go to https://render.com
2. Sign up with GitHub
3. New+ → Web Service
4. Connect: piyush1418/ai-proctoring
5. Settings:
   - Build: ./build.sh
   - Start: gunicorn futurproctor.wsgi:application
6. Deploy (takes 10 min)

### Option 3: PythonAnywhere (Manual but Reliable)
1. Sign up: https://www.pythonanywhere.com
2. Upload project ZIP
3. Bash console:
   ```bash
   unzip futurproctor.zip
   cd futurproctor
   pip3 install --user -r requirements.txt
   python3 manage.py migrate --skip-checks
   python3 manage.py collectstatic --noinput
   ```
4. Web tab → Manual config → Python 3.10
5. Set paths and reload

### Option 4: Vercel (Fastest)
1. Install: npm i -g vercel
2. Run in project: vercel
3. Follow prompts
4. Get instant URL

## Your GitHub Repo
https://github.com/piyush1418/ai-proctoring

## Files Ready for Deployment
✓ requirements.txt
✓ build.sh
✓ Procfile
✓ render.yaml
✓ runtime.txt
✓ settings.py (production-ready)

## Recommended: Railway
- Fastest deployment
- Auto-detects everything
- Free tier available
- Public URL in 2 minutes
