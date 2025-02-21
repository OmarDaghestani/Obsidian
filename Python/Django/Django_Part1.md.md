## Part 1: Creating a Project

### Key Concepts

#### Django Project Structure
- `django-admin startproject mysite`: Creates a project named `mysite`.
- **Outer `mysite/`**: Holds `manage.py` (command-line tool).
- **Inner `mysite/`**: Contains:
  - `settings.py` (settings)
  - `urls.py` (URLs)
  - App configurations

#### Development Server
- `python manage.py runserver`: Starts a lightweight server at `http://127.0.0.1:8000/`.
- Stop with `Ctrl+C`; add a port (e.g., `8080`) if needed.

#### Purpose
- Sets up the foundation for your app; no functionality yet, just a skeleton.

### Must-Know
- Always run commands from the directory with `manage.py`.
- **Git Bash**: Use `python` or `python3` based on what works for your setup.

### Moving Forward
- Every Django project needs this structure. You’ll build apps (like `polls`) inside it.


## Next: [[Django_Part2.md]]

#django, #tutorial, #python