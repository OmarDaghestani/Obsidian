# Part 7 - Customizing the Admin

## Overview
Part 7 enhances the Django admin interface for the polls app, improving usability and organization. This aligns with [[Interactive Full-Stack Project]]’s “professional” presentation goals by refining backend management.

## Key Concepts
- **Admin Customization**: Modify `polls/admin.py` for better data handling.
- **Inlines**: Edit `Choice` within `Question` forms.
- **Fieldsets**: Group and collapse fields.
- **Filters/Search**: Add navigation tools to the list view.

## Must-Know
- **Inline**: `TabularInline` embeds related models.
- **Fieldsets**: Organize fields with optional `collapse`.
- **List Options**: `list_filter`, `search_fields` enhance list usability.
- **Run**: `python manage.py runserver` to test.

## Code Example

### Admin (`polls/admin.py`)
```python
from django.contrib import admin
from .models import Question, Choice

class ChoiceInline(admin.TabularInline):
    model = Choice
    extra = 3

class QuestionAdmin(admin.ModelAdmin):
    list_display = ('question_text', 'pub_date', 'was_published_recently')
    inlines = [ChoiceInline]
    fieldsets = [
        (None,               {'fields': ['question_text']}),
        ('Date information', {'fields': ['pub_date'], 'classes': ['collapse']}),
    ]
    list_filter = ['pub_date']
    search_fields = ['question_text']

admin.site.register(Question, QuestionAdmin)