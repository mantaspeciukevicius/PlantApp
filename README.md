# Plant App

A Flask coursework application for managing plants, plant groups, watering records, departments and projects, with user authentication and role-aware routes.

## Origin

**Original creation date: 25 February 2023.** The GitHub repository and its earliest recorded commit date to this day.

The original application was created by Mantas Peciukevičius during the **Code Academy course, without AI assistance**. This statement describes the original coursework; the portfolio documentation was refreshed later. The project builds on the author’s earlier bill-splitting coursework, as recorded in its first commit.

## Features in the source

- User registration, login/logout and profile pages.
- Plant groups, individual plants, editing and deletion.
- Plant watering history and group-to-user assignments.
- Departments, projects and their relationships.
- Earlier bill/group models retained from the source application.
- Form validation and JWT-based route authorization helpers.

This repository documents a historical course project. The feature list reflects the source, rather than a claim that every workflow has been verified on current dependencies.

## Technology stack

| Layer | Technologies |
| --- | --- |
| Language / web framework | Python, Flask 2.2.3, Flask blueprints and application factory |
| Database | SQLite, SQLAlchemy 1.4.46, Flask-SQLAlchemy 3.0.2 |
| Authentication | Flask-Login, Werkzeug password hashing, PyJWT |
| Forms | WTForms, Flask-WTF |
| Templates / styling | Jinja2, HTML/CSS, Bulma and Bootstrap |
| Database migrations | Flask-Migrate and Alembic |
| HTTP requests | Requests |

Exact historical dependencies are listed in `requirements.txt`. Flask-Script is also present in the older migration helper; the normal application entry point is the Flask factory.

## Run locally

Use a fresh Python 3.10 virtual environment rather than a previously committed environment or database:

```sh
python3.10 -m venv .venv
# Linux / macOS
. .venv/bin/activate
# Windows PowerShell: .venv\Scripts\Activate.ps1
pip install -r requirements.txt
python -c "from project import create_app, db; app = create_app(); app.app_context().push(); db.create_all()"
flask --app project run --host 127.0.0.1
```

Open `http://127.0.0.1:5000` and register your own local test account. Review account roles in the source when testing management routes. Set a fresh Flask secret key before using the app beyond a local coursework demonstration.

## Repository layout

- `project/__init__.py`: application factory, extension setup and blueprint registration.
- `project/auth.py`: account and authorization routes.
- `project/plants.py`: plant and plant-group workflows.
- `project/departments.py`: departments and projects.
- `project/models.py`: SQLAlchemy models and relationships.
- `project/templates/`: Jinja pages.

Runtime databases and credentials are not required to understand this project. Create a new database locally; do not publish account data or environment files.
