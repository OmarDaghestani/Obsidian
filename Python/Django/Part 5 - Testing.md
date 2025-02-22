# Part 5 - Testing

## Overview
Part 5 enhances the polls app with automated tests and introduces Django’s generic views for cleaner, more efficient code. We test model logic and view behavior, ensuring the app works reliably while aligning with [[Interactive Full-Stack Project]]’s “good-quality coding standards.”

## Key Concepts
- **Testing**: Automated tests in `polls/tests.py` using Django’s `TestCase`.
  - Tests `Question.was_published_recently()` for time-based logic.
  - Verifies `IndexView` and `DetailView` behavior for question visibility.
- **Generic Views**: Replace function-based views with class-based views (`ListView`, `DetailView`).
  - Filters out unpublished questions (`pub_date__lte=timezone.now()`).
- **Admin Enhancements**: Adds `was_published_recently` to the admin list view.
- **URL Namespacing**: Uses `app_name` for robust URL reversing.

## Must-Know
- **Run Tests**: `python manage.py test polls` runs all tests (10 total with additions).
- **Test Database**: Django creates a temporary database, preserving real data.
- **Generic Views**: Use `as_view()` in URLs and customize with `get_queryset()`.
- **Assertions**: `assertIs`, `assertEqual`, `assertContains`, `assertQuerySetEqual` for validation.
- **Namespace**: `app_name = 'polls'` enables `reverse('polls:index')`.

## Code Examples

### Models (`polls/models.py`)
Defines the data structure and adds `was_published_recently()`:
```python
from django.db import models
from django.utils import timezone
import datetime

class Question(models.Model):
    question_text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('date published')

    def __str__(self):
        return self.question_text
    
    def was_published_recently(self):
        now = timezone.now()
        return now - datetime.timedelta(days=1) <= self.pub_date <= now

class Choice(models.Model):
    question = models.ForeignKey(Question, on_delete=models.CASCADE)
    choice_text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)

    def __str__(self):
        return self.choice_text
```



### Tests (`polls/tests.py`)
Tests model logic and view behavior:
```python
import datetime
from django.test import TestCase
from django.utils import timezone
from django.urls import reverse
from .models import Question

# Model Tests
class QuestionModelTests(TestCase):
    def test_was_published_recently_with_future_question(self):
        """was_published_recently() returns False for future questions."""
        time = timezone.now() + datetime.timedelta(days=30)
        future_question = Question(pub_date=time)
        self.assertIs(future_question.was_published_recently(), False)

    def test_was_published_recently_with_old_question(self):
        """was_published_recently() returns False for questions older than 1 day."""
        time = timezone.now() - datetime.timedelta(days=1, seconds=1)
        old_question = Question(pub_date=time)
        self.assertIs(old_question.was_published_recently(), False)

    def test_was_published_recently_with_recent_question(self):
        """was_published_recently() returns True for questions within 24 hours."""
        time = timezone.now() - datetime.timedelta(hours=23, minutes=59, seconds=59)
        recent_question = Question(pub_date=time)
        self.assertIs(recent_question.was_published_recently(), True)

# Helper Function
def create_question(question_text, days):
    """Create a question with given text and days offset from now."""
    time = timezone.now() + datetime.timedelta(days=days)
    return Question.objects.create(question_text=question_text, pub_date=time)

# Index View Tests
class QuestionIndexViewTests(TestCase):
    def test_no_questions(self):
        """If no questions exist, show 'No polls are available.'"""
        response = self.client.get(reverse('polls:index'))
        self.assertEqual(response.status_code, 200)
        self.assertContains(response, "No polls are available.")
        self.assertQuerySetEqual(response.context['latest_question_list'], [])

    def test_past_question(self):
        """Past questions are displayed."""
        question = create_question("Past question.", days=-30)
        response = self.client.get(reverse('polls:index'))
        self.assertQuerySetEqual(response.context['latest_question_list'], [question])

    def test_future_question(self):
        """Future questions are excluded."""
        create_question("Future question.", days=30)
        response = self.client.get(reverse('polls:index'))
        self.assertContains(response, "No polls are available.")
        self.assertQuerySetEqual(response.context['latest_question_list'], [])

    def test_future_and_past_questions(self):
        """Only past questions are shown."""
        past_q = create_question("Past question.", days=-30)
        create_question("Future question.", days=30)
        response = self.client.get(reverse('polls:index'))
        self.assertQuerySetEqual(response.context['latest_question_list'], [past_q])

    def test_two_past_questions(self):
        """Multiple past questions are displayed, ordered by recency."""
        q1 = create_question("Past question 1.", days=-5)
        q2 = create_question("Past question 2.", days=-30)
        response = self.client.get(reverse('polls:index'))
        self.assertQuerySetEqual(response.context['latest_question_list'], [q1, q2])

# Detail View Tests
class QuestionDetailViewTests(TestCase):
    def test_future_question(self):
        """Detail view of future question returns 404."""
        future_q = create_question("Future question.", days=5)
        response = self.client.get(reverse('polls:detail', args=(future_q.id,)))
        self.assertEqual(response.status_code, 404)

    def test_past_question(self):
        """Detail view of past question shows its text."""
        past_q = create_question("Past question.", days=-5)
        response = self.client.get(reverse('polls:detail', args=(past_q.id,)))
        self.assertEqual(response.status_code, 200)
        self.assertContains(response, past_q.question_text)
```

#django, #tutorial, #python 


### Views (`polls/views.py`)
Tests model logic and view behavior:
```python
from django.shortcuts import get_object_or_404, render, redirect
from django.views import generic
from django.utils import timezone
from .models import Question, Choice

class IndexView(generic.ListView):
    template_name = 'polls/index.html'
    context_object_name = 'latest_question_list'

    def get_queryset(self):
        """Return the last five published questions."""
        return Question.objects.filter(pub_date__lte=timezone.now()).order_by('-pub_date')[:5]

class DetailView(generic.DetailView):
    model = Question
    template_name = 'polls/detail.html'

    def get_queryset(self):
        """Excludes unpublished questions."""
        return Question.objects.filter(pub_date__lte=timezone.now())

class ResultsView(generic.DetailView):
    model = Question
    template_name = 'polls/results.html'

def vote(request, question_id):
    question = get_object_or_404(Question, pk=question_id)
    try:
        selected_choice = question.choice_set.get(pk=request.POST['choice'])
    except (KeyError, Choice.DoesNotExist):
        return render(request, 'polls/detail.html', {
            'question': question,
            'error_message': "You didn't select a choice.",
        })
    else:
        selected_choice.votes += 1
        selected_choice.save()
        return redirect('results', question_id=question_id)
```


### URLS (`polls/urls.py`)
```python
from django.urls import path
from . import views

app_name = 'polls'
urlpatterns = [
    path('', views.IndexView.as_view(), name='index'),
    path('<int:pk>/', views.DetailView.as_view(), name='detail'),
    path('<int:pk>/results/', views.ResultsView.as_view(), name='results'),
    path('<int:question_id>/vote/', views.vote, name='vote'),
]
```



### Admin (`polls/admin.py`)
```python
from django.contrib import admin
from .models import Question, Choice

class QuestionAdmin(admin.ModelAdmin):
    list_display = ('question_text', 'pub_date', 'was_published_recently')

admin.site.register(Question, QuestionAdmin)
admin.site.register(Choice)
```





## FBVs vs. Generic CBVs
**Function-Based Views (FBVs):**
- Simple functions taking request and returning HttpResponse.
- Example (old detail):

```python
def detail(request, question_id):
    question = get_object_or_404(Question, pk=question_id)
    return render(request, 'polls/detail.html', {'question': question})
```

- **Pros**: Simple, full control, flexible.
- **Cons**: Verbose, repetitive for common tasks


**Generic Class-Based Views (CBVs)**:  

- Classes inheriting from generic.ListView, generic.DetailView, etc.
- Example (DetailView):

```python
class DetailView(generic.DetailView):
    model = Question
    template_name = 'polls/detail.html'
    def get_queryset(self):
        return Question.objects.filter(pub_date__lte=timezone.now())
```

- **Pros**: Concise, reusable, built-in functionality (e.g., 404 handling).
- **Cons**: Steeper learning curve, less flexibility for complex logic.


**Differences**:  
- **Syntax**: FBVs are functions; CBVs are classes with attributes/methods.
- **Code**: FBVs need manual logic; CBVs automate common patterns.
- **Use**: FBVs for custom tasks (e.g., **vote**); CBVs for CRUD (e.g., **index**, **detail**).

## FBVs vs. Generic CBVs Table
Below is a detailed comparison of FBVs and Generic CBVs:

| Aspect              | Function-Based Views (FBVs)                  | Generic Class-Based Views (CBVs)            |
|---------------------|---------------------------------------------|--------------------------------------------|
| **Syntax**          | Simple function: `def view(request, args):` | Class: `class ViewName(GenericView):`      |
| **Code Length**     | More verbose; explicit logic required       | Concise; leverages built-in functionality  |
| **Ease of Use**     | Easier for beginners, direct control        | Steeper learning curve but more efficient  |
| **Reusability**     | Must rewrite similar logic                  | Inherently reusable via inheritance        |
| **Customization**   | Fully flexible, no constraints              | Flexible via method overrides, structured  |
| **Common Tasks**    | Manual (e.g., `get_object_or_404`)          | Automated (e.g., `DetailView` handles 404) |
| **Maintenance**     | Harder to scale with complexity             | Easier to maintain for larger projects     |



#django, #tutorial, #python 

## Previous: [[Part 4 - Templates and Forms]]
## Next: [[Part 6 - Static Files]]
