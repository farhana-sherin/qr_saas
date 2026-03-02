# QR-SaaS Project

This repository contains the backend and frontend for the QR-SaaS application.

## 🛠️ Environment Setup (Backend)

Follow these steps to prepare a Python development environment and run the Django backend.

### 1. Clone the repository

```bash
git clone https://github.com/your-org/qr-saas.git
cd qr-saas/backend
```

### 2. Create a Python virtual environment

This project assumes Python 3.11+ (adjust version if needed).

```bash
# Windows (PowerShell)
python -m venv .venv
.\.venv\Scripts\Activate.ps1

# macOS/Linux
python3 -m venv .venv
source .venv/bin/activate
```

> ⚠️ Always activate the virtual environment before installing packages or running Django commands.

### 3. Install Python dependencies

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

Dependencies include Django and any other libraries used in the `backend/apps`.

### 4. Configure settings

The settings are split into `base.py`, `dev.py`, and `prod.py` under `backend/config/settings/`.

- `dev.py` is used for local development and loads environment variables from `.env`.
- Create a `.env` file in `backend/` with keys such as:
  ```ini
  SECRET_KEY=your-secret-key
  DEBUG=True
  ALLOWED_HOSTS=localhost,127.0.0.1
  DATABASE_URL=sqlite:///db.sqlite3
  ```

> 💡 For production, set `DJANGO_SETTINGS_MODULE=config.settings.prod` and provide secure values.

### 5. Initialize the database

```bash
python manage.py migrate
```

If using SQLite (default) the file `db.sqlite3` will be created under `backend/config`.

### 6. Create a superuser (optional)

```bash
python manage.py createsuperuser
```

### 7. Run the development server

```bash
python manage.py runserver
```
Visit `http://127.0.0.1:8000` in your browser.

## 🏗️ Workspace Structure

```
backend/
  manage.py
  requirements.txt
  apps/
    accounts/
    common/
    qr_codes/
  config/
    settings/
      base.py
      dev.py
      prod.py
frontend/
  ...
```

## ⚙️ Frontend

Instructions for setting up the frontend should go here (e.g. Node.js version, install dependencies, run local dev server). Adapt according to actual setup.

## 🚀 Additional Notes

- When checking out a new branch or pulling updates, re-run `pip install -r requirements.txt` if dependencies change.
- Run tests with: `python manage.py test` from `backend/`.

---

Happy hacking! 🎉
