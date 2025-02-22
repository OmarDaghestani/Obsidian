# Responsibilities

## Project Files (`mysite/`)
- **`db.sqlite3`**: SQLite database storing `Question`, `Choice`, and Django tables.
- **`manage.py`**: Command-line tool for migrations, server, tests, etc.
- **`mysite/__init__.py`**: Marks as Python package.
- **`mysite/settings.py`**: Configures apps, database, static files.
- **`mysite/urls.py`**: Routes requests to apps or admin.
- **`mysite/asgi.py`, `wsgi.py`**: Deployment entry points.

## App Files (`polls/`)
- **`__init__.py`**: Marks as Python package.
- **`apps.py`**: Configures `PollsConfig`.
- **`models.py`**: Defines `Question`, `Choice` models.
- **`admin.py`**: Customizes admin for data management.
- **`views.py`**: Handles requests (FBVs or generic CBVs).
- **`urls.py`**: Maps URLs to views.
- **`tests.py`**: Tests models and views.
- **`templates/polls/`**: HTML for dynamic content.
- **`static/polls/`**: CSS, JS, images for styling.
- **`migrations/`**: Tracks database changes.

## Process
- User request → `urls.py` → `views.py` → `models.py` (data) → `templates/` (render) + `static/` (style).
- Data managed via `admin.py`, stored in `db.sqlite3`, tested in `tests.py`.

## Tags
#django #files #structure #bootcamp