# Part 4 - Templates and Forms

## Key Concepts
- **Templates**: HTML files in `polls/templates/polls/` for dynamic content.
  - `index.html`: Lists latest questions.
  - `detail.html`: Shows question and voting form.
  - `results.html`: Displays vote results.
- **Views**: Updated to use `render` and fetch data.
  - `index`: Shows 5 recent questions.
  - `detail`: Gets question by ID or 404.
  - `vote`: Handles form submission, updates votes.
  - `results`: Shows vote tally.
- **Forms**: Added a voting form in `detail.html` with POST action.

## Must-Know
- **Template Syntax**: `{% %}` for logic, `{{ }}` for variables (e.g., `{{ question.question_text }}`).
- **CSRF Token**: `{% csrf_token %}` required for POST forms.
- **Database**: Add data via [[Part 2 - Models and Admin]] admin panel (`/admin/`).
- **Redirect**: `redirect()` moves users after voting.

## Setup
- Directory: `polls/templates/polls/`.
- Commands:
  - `python manage.py runserver` to test.
- URLs:
  - `/polls/`: Index.
  - `/polls/<id>/`: Detail.
  - `/polls/<id>/vote/`: Vote action.
  - `/polls/<id>/results/`: Results.

## Next
- [[Part 5 - Testing]] to ensure functionality.

## Notes
- Admin registration (`polls/admin.py`) is critical:
  ```python
  from django.contrib import admin
  from .models import Question, Choice

  admin.site.register(Question)
  admin.site.register(Choice)
  ```

#django, #tutorial, #python 

## Previous: [[Part 3 - Views and URLs]]

## Next: [[Part 5 - Testing]]

