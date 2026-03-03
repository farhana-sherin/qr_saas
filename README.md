🚀 **QR-SaaS Project**

A full-stack SaaS platform for generating and managing QR codes.

> **Note:** This README is annotated with comments to help newcomers quickly understand the structure and important commands.

This repository contains two main pieces:

- 🧠 **Django Backend (API)** – serves data and business logic
- 🎨 **Frontend (React / Next / etc.)** – user interface

📁 **Project Structure** (top-level overview)
```
qr-saas/
│
├── backend/            # Django backend application
│   ├── manage.py       # Entry point for Django commands
│   ├── requirements.txt  # Python dependencies
│   ├── apps/           # Django apps (accounts, common, qr_codes)
│   │   ├── accounts/
│   │   ├── common/
│   │   └── qr_codes/
│   └── config/         # Project configuration
│       └── settings/   # Settings split by environment
│           ├── base.py
│           ├── dev.py
│           └── prod.py
│
└── frontend/           # React/Vite frontend code
```

> ✅ **Tip:** Start by looking at the `backend/README` or relevant docs in each app when working on a specific area.
🛠 **Backend Setup Guide (For New Developers)**

1️⃣ **Clone Repository**
```bash
git clone https://github.com/your-org/qr-saas.git
cd qr-saas/backend
```
> This places you in the backend folder where all Django commands should be executed.

2️⃣ **Create Virtual Environment**

*Windows (PowerShell)*
```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```
*macOS / Linux*
```bash
python3 -m venv .venv
source .venv/bin/activate
```

⚠ **Important:** Always activate the virtual environment before running Django. You can tell it's active if your prompt is prefixed with `(.venv)`.

3️⃣ **Install Dependencies**
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

4️⃣ **Create `.env` File**

Inside `backend/` create a file named `.env` with your configuration.

> Example development configuration (do **not** commit this file):
```
SECRET_KEY=your-secret-key
DEBUG=True
DJANGO_SETTINGS_MODULE=config.settings.dev

DB_ENGINE=django.db.backends.sqlite3
DB_NAME=db.sqlite3
DB_USER=
DB_PASSWORD=
DB_HOST=
DB_PORT=
```

5️⃣ **Run Migrations**
```bash
python manage.py makemigrations
python manage.py migrate
```

6️⃣ **Create Superuser**
```bash
python manage.py createsuperuser
```

7️⃣ **Run Development Server**
```bash
python manage.py runserver
```

📍 The backend will be available at:
```
http://127.0.0.1:8000
```

🌿 **Git Workflow (Team Collaboration Guide)**

> We use a simple *dev branch* workflow to isolate features.

🔹 **First Time Setup**

After cloning the repo for the first time run:
```bash
git checkout dev
git pull origin dev
```
This ensures your local `dev` matches the remote.

🌱 **Creating a New Feature Branch**

Always branch **from `dev`**, never from `main`.
```bash
git checkout dev
git pull origin dev
git checkout -b feature/feature-name
```
> Example branch name: `feature/jwt-authentication`

💾 **Commit Changes**
```bash
git add .
git commit -m "Added JWT authentication"
```
Keep commit messages descriptive and reference tickets if possible.

⬆ **Push Branch**
```bash
git push origin feature/feature-name
```
Then open a Pull Request (PR) targeting `dev`. Wait for review and merge.

🔄 **Updating Your Branch with Latest `dev`**

If `dev` gets new commits while you work:
```bash
git checkout dev
git pull origin dev

git checkout feature/your-branch
git merge dev
```
Resolve any conflicts and test locally.

🔁 **Pull Latest Changes**

Before you start work each day:
```bash
git checkout dev
git pull origin dev
```
This keeps your environment up to date.

🔀 **Merge `dev` into `main` (Production)**

Only done by release managers after thorough testing:
```bash
git checkout main
git pull origin main
git merge dev
git push origin main
```
🏭 **Production Setup**

> These steps are for the live server only; developers should not run them locally.

On the production machine set the environment variable:
```bash
export DJANGO_SETTINGS_MODULE=config.settings.prod
```

Production `.env` example (store securely):
```
SECRET_KEY=secure-production-key
DEBUG=False
DJANGO_SETTINGS_MODULE=config.settings.prod

DB_ENGINE=django.db.backends.postgresql
DB_NAME=qr_saas
DB_USER=postgres
DB_PASSWORD=yourpassword
DB_HOST=localhost
DB_PORT=5432
```

> 💡 Use a managed secret store or vault – do **not** check this file into source control.

🧪 **Run Tests**
```bash
python manage.py test
```
Run this before pushing major changes to ensure nothing breaks.

📦 **Installing New Packages**
After you add a new dependency, update the requirements file:
```bash
pip freeze > requirements.txt
git add requirements.txt
git commit -m "Updated requirements"
```
This keeps all developers and deployment environments in sync.
