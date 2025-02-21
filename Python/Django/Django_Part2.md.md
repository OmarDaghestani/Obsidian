## Part 2: Models and Admin

### Key Concepts

#### Apps
- `python manage.py startapp polls`: Creates an app (`polls`) for specific functionality.
- Add to `INSTALLED_APPS` in `settings.py` (e.g., `'polls.apps.PollsConfig'`).

#### Models
- Defined in `polls/models.py`:
  - **Question**: 
    - `question_text` (CharField)
    - `pub_date` (DateTimeField)
  - **Choice**: 
    - `question` (ForeignKey to Question)
    - `choice_text` (CharField)
    - `votes` (IntegerField)
- `__str__`: Makes models readable in admin/shell (e.g., returns `question_text`).

#### Database
- `python manage.py makemigrations`: Creates migration files from model changes.
- `python manage.py migrate`: Applies migrations to the database (SQLite by default).

#### Shell
- `python manage.py shell`: Interactive Python environment to test models.
- Example: `Question.objects.all()` queries the database.

#### Admin Interface
- `python manage.py createsuperuser`: Sets up an admin user.
- Register models in `polls/admin.py` (e.g., `admin.site.register(Question)`).
- Access at `http://127.0.0.1:8000/admin/` to manage data.

### Must-Know
- **Migrations**: Always run `makemigrations` and `migrate` after changing models.
- **Admin**: Superuser credentials are your key to managing data; keep them safe.
- **Models**: Define your database structure—think of them as blueprints.
- **SQLite**: Default database; no separate setup needed for now.

### Moving Forward
- **Database Changes**: If you tweak models later, repeat the migration process.
- **Admin**: Use it to test and manage data as you add views and URLs.
- **App Separation**: Each app (like `polls`) should handle a distinct feature—keep this modular mindset.

#django, #tutorial, #python


## Previous: [[Django_Part1.md]]
## Next: [[Django_Part3.md]]
