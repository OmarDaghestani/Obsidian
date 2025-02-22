# Part 3 - Views and URLs

## Key Concepts
- **Views**: Functions in `polls/views.py` return `HttpResponse`.
  - `index`, `detail`, `results`, `vote` with `question_id`.
- **URLs**: 
  - `polls/urls.py` maps views to paths (e.g., `<int:question_id>/`).
  - `mysite/urls.py` uses `include()` for `polls/` routes.

## Must-Know
- URL patterns use `<int:parameter>` for dynamic routing.
- Test at `http://127.0.0.1:8000/polls/`.

## Next
- Templates in Part 4 will use these views.

## Commands
- `python manage.py runserver`

#django, #tutorial, #python
## Previous: [[Part 2 - Models and Admin]]

## Next: [[Part 4 - Templates and Forms]]
