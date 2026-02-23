# ✅ DEPLOYMENT CHECKLIST - STEP BY STEP

## **Phase 1: GitHub Setup (No code needed, just web UI)**

### Step 1: Go to GitHub and Create Account
1. Open https://github.com
2. Sign up (or login if you have account)
3. Verify your email

### Step 2: Create New Repository
1. Click the **+** icon (top right)
2. Select "New repository"
3. Fill in:
   - **Repository name**: `exam-proctoring-system`
   - **Description**: AI-Based Online Exam Proctoring System
   - **Public** (select this)
   - **Skip** "Initialize with README"
4. Click **Create repository**

### Step 3: Upload Your Project Files
1. On your empty repository, click **Add file** → **Upload files**
2. **IMPORTANT**: Only upload files from this location:
   ```
   c:\Users\piyus\Downloads\AI-Based-online-exam-proctoring-System-main\
   AI-Based-online-exam-proctoring-System-main\futurproctor\
   ```
   
   Upload these files/folders:
   - ✅ futurproctor/ (folder with settings.py, wsgi.py, urls.py)
   - ✅ proctoring/ (folder with models, views, etc)
   - ✅ static/ (folder)
   - ✅ media/ (folder)
   - ✅ templates/ (folder)
   - ✅ migrations/ (folder)
   - ✅ db.sqlite3
   - ✅ manage.py
   - ✅ requirements.txt
   - ✅ Procfile
   - ✅ runtime.txt
   - ✅ build.sh
   - ✅ render.yaml

3. Add commit message: "Initial commit"
4. Click **Commit changes**

### Step 4: Verify Upload
- Navigate to your repository
- You should see all files listed
- Check that `manage.py` and `requirements.txt` are visible

---

## **Phase 2: Render Deployment**

### Step 1: Create Render Account
1. Go to https://render.com
2. Click **Sign up**
3. Select **Continue with GitHub**
4. Authorize Render to access your GitHub

### Step 2: Create Web Service
1. In Render Dashboard, click **New +**
2. Select **Web Service**
3. Find and select your `exam-proctoring-system` repository
4. Click **Connect**

### Step 3: Configure Service
Fill in these fields:

- **Name**: `exam-proctoring` (this becomes your URL)
- **Environment**: Python 3
- **Region**: US East (or closest to you)
- **Branch**: main
- **Build Command**: 
  ```
  pip install -r requirements.txt && python manage.py collectstatic --no-input && python manage.py migrate --skip-checks
  ```
- **Start Command**: 
  ```
  gunicorn futurproctor.wsgi:application --bind 0.0.0.0:$PORT
  ```
- **Plan**: Free

### Step 4: Set Environment Variables
1. Scroll to **Environment**
2. Add these variables:

```
SECRET_KEY=django-insecure-your-random-secret-key-12345
DEBUG=False
ALLOWED_HOSTS=exam-proctoring.onrender.com
PYTHON_VERSION=3.10.0
```

3. Click **Add**

### Step 5: Deploy
1. Click **Create Web Service**
2. Wait for build to complete (5-15 minutes)
3. Monitor in the **Logs** tab

### Step 6: Get Your Live URL
- Once build succeeds, you'll see:
  ```
  https://exam-proctoring.onrender.com
  ```
- Copy this URL - that's your live application!

---

## **Phase 3: Testing**

### Test Your Deployment
1. Open the URL: https://exam-proctoring.onrender.com
2. Should see login page
3. Check functionality

### If It Fails
1. Go to Render Dashboard → Your Service → **Logs**
2. Look for error messages
3. Common issues:
   - Missing environment variables
   - Import errors (check requirements.txt)
   - Database errors (fixed in this version)

---

## **IMPORTANT NOTES**

⚠️ **Backend URL Structure**
- The app runs from root `/` 
- Admin panel: `https://exam-proctoring.onrender.com/admin/`
- Login: `https://exam-proctoring.onrender.com/login/`

⚠️ **Email Configuration**
- If you need email (password reset, notifications):
  - Add `EMAIL_BACKEND` to environment
  - Use Gmail or SendGrid (recommended)

⚠️ **Static Files**
- Automatically collected and served
- May take 1-2 minutes to appear

---

## **POST-DEPLOYMENT**

### Create Admin User
1. In Render dashboard, go to **Shell** tab
2. Run:
   ```bash
   python manage.py createsuperuser
   ```
3. Fill in username, email, password
4. Login at: `https://exam-proctoring.onrender.com/admin/`

### Database Note
- Using SQLite (suitable for small deployments)
- For production with many users, upgrade to PostgreSQL

---

**Your deployment URL will be:**
```
https://exam-proctoring.onrender.com
```

**Share this with users to access the exam system!**
