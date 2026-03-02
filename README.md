🚀 QR-SaaS Project

A full-stack SaaS platform for generating and managing QR codes.

This repository contains:

🧠 Django Backend (API)

🎨 Frontend (React / Next / etc.)

📁 Project Structure
qr-saas/
│
├── backend/
│   ├── manage.py
│   ├── requirements.txt
│   ├── apps/
│   │   ├── accounts/
│   │   ├── common/
│   │   └── qr_codes/
│   └── config/
│       └── settings/
│           ├── base.py
│           ├── dev.py
│           └── prod.py
│
└── frontend/
🛠 Backend Setup Guide (For New Developers)
1️⃣ Clone Repository
git clone https://github.com/your-org/qr-saas.git
cd qr-saas/backend
2️⃣ Create Virtual Environment
Windows (PowerShell)
python -m venv .venv
.\.venv\Scripts\Activate.ps1
macOS / Linux
python3 -m venv .venv
source .venv/bin/activate

⚠ Always activate the virtual environment before running Django.

3️⃣ Install Dependencies
pip install --upgrade pip
pip install -r requirements.txt
4️⃣ Create .env File

Inside backend/ create a file named:

.env

Example development configuration:

SECRET_KEY=your-secret-key
DEBUG=True
DJANGO_SETTINGS_MODULE=config.settings.dev

DB_ENGINE=django.db.backends.sqlite3
DB_NAME=db.sqlite3
DB_USER=
DB_PASSWORD=
DB_HOST=
DB_PORT=
5️⃣ Run Migrations
python manage.py makemigrations
python manage.py migrate
6️⃣ Create Superuser
python manage.py createsuperuser
7️⃣ Run Development Server
python manage.py runserver

Backend runs at:

http://127.0.0.1:8000
🌿 Git Workflow (Team Collaboration Guide)

We follow a dev branch workflow.

🔹 First Time Setup

After cloning:

git checkout dev
git pull origin dev
🌱 Creating a New Feature Branch

Always create a branch from dev.

git checkout dev
git pull origin dev
git checkout -b feature/feature-name

Example:

git checkout -b feature/jwt-authentication
💾 Commit Changes
git add .
git commit -m "Added JWT authentication"
⬆ Push Branch
git push origin feature/feature-name

Then create a Pull Request → Merge into dev.

🔄 Updating Your Branch with Latest Dev

If dev was updated:

git checkout dev
git pull origin dev

git checkout feature/your-branch
git merge dev

Resolve conflicts if any.

🔁 Pull Latest Changes

Before starting work daily:

git checkout dev
git pull origin dev
🔀 Merge dev into main (Production)

Only after testing:

git checkout main
git pull origin main
git merge dev
git push origin main
🏭 Production Setup

On production server:

export DJANGO_SETTINGS_MODULE=config.settings.prod

Production .env example:

SECRET_KEY=secure-production-key
DEBUG=False
DJANGO_SETTINGS_MODULE=config.settings.prod

DB_ENGINE=django.db.backends.postgresql
DB_NAME=qr_saas
DB_USER=postgres
DB_PASSWORD=yourpassword
DB_HOST=localhost
DB_PORT=5432
🧪 Run Tests
python manage.py test
📦 Installing New Packages

After installing new packages:

pip freeze > requirements.txt
git add requirements.txt
git commit -m "Updated requirements"