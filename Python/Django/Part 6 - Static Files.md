# Part 6 - Static Files

## Overview
Part 6 enhances the polls app’s UI with static files (CSS), meeting [[Interactive Full-Stack Project]]’s “polished UI” and “responsive” requirements through basic styling.

## Key Concepts
- **Static Files**: CSS, JS, images in `polls/static/polls/`.
- **Template Integration**: `{% load static %}` and `{% static %}` link files.
- **Settings**: `STATIC_URL` and `STATICFILES_DIRS` configure static handling.

## Must-Know
- **Directory**: `polls/static/polls/` namespaces files.
- **Static Tag**: `{% load static %}` at template top; `{% static 'path' %}` for paths.
- **Development**: `STATICFILES_DIRS` works in dev; production uses `collectstatic`.


## Step-by-Step

### Create Static Directory
```bash
mkdir polls/static
mkdir polls/static/polls
```

### Add CSS (polls/static/polls/style.css)

```css
body {
    background-color: #f0f0f0;
    font-family: Arial, sans-serif;
}

li a {
    color: #007bff;
    text-decoration: none;
}

li a:hover {
    text-decoration: underline;
}

h1 {
    color: #333;
}

ul {
    list-style-type: none;
    padding: 0;
}

form {
    margin: 20px 0;
}

input[type="submit"] {
    background-color: #007bff;
    color: white;
    padding: 8px 16px;
    border: none;
    cursor: pointer;
}

input[type="submit"]:hover {
    background-color: #0056b3;
}
```

### Configure Settings (mysite/settings.py)

```python
STATIC_URL = '/static/'
STATICFILES_DIRS = [
    BASE_DIR / "polls" / "static",
]
```

### Update Templates

- **Index (polls/templates/polls/index.html)**:
```html
{% load static %}

<!DOCTYPE html>
<html>
<head>
    <title>Polls</title>
    <link rel="stylesheet" href="{% static 'polls/style.css' %}">
</head>
<body>
    {% if latest_question_list %}
        <ul>
        {% for question in latest_question_list %}
            <li><a href="{% url 'polls:detail' question.id %}">{{ question.question_text }}</a></li>
        {% endfor %}
        </ul>
    {% else %}
        <p>No polls are available.</p>
    {% endif %}
</body>
</html>
```

**Detail (polls/templates/polls/detail.html)**:
```html
{% load static %}

<!DOCTYPE html>
<html>
<head>
    <title>{{ question.question_text }}</title>
    <link rel="stylesheet" href="{% static 'polls/style.css' %}">
</head>
<body>
    <h1>{{ question.question_text }}</h1>

    {% if error_message %}<p><strong>{{ error_message }}</strong></p>{% endif %}

    <form action="{% url 'polls:vote' question.id %}" method="post">
    {% csrf_token %}
    <ul>
    {% for choice in question.choice_set.all %}
        <li>
            <input type="radio" name="choice" id="choice{{ forloop.counter }}" value="{{ choice.id }}">
            <label for="choice{{ forloop.counter }}">{{ choice.choice_text }}</label>
        </li>
    {% endfor %}
    </ul>
    <input type="submit" value="Vote">
    </form>
</body>
</html>
```

**Results (polls/templates/polls/results.html)**:
```html
{% load static %}

<!DOCTYPE html>
<html>
<head>
    <title>Results - {{ question.question_text }}</title>
    <link rel="stylesheet" href="{% static 'polls/style.css' %}">
</head>
<body>
    <h1>{{ question.question_text }}</h1>
    <ul>
    {% for choice in question.choice_set.all %}
        <li>{{ choice.choice_text }} -- {{ choice.votes }} vote{{ choice.votes|pluralize }}</li>
    {% endfor %}
    </ul>
    <a href="{% url 'polls:detail' question.id %}">Vote again?</a>
</body>
</html>
```

### Test
- Run: python `manage.py runserver`
- URLs: `/polls/, /polls/<id>/, /polls/<id>/results/`



#django, #tutorial, #python 

## Previous: [[Part 5 - Testing]]
## Next: [[Part 7 - Customizing the Admin]]



