---
title: 'Django Project - Quickstart Guide Part 2'
date: 2020-04-16T11:50:30-04:00
categories:
  - Quickstart Guide
tags:
  - QSG
  - Django
---

## Creating views, templates, and connecting them to urls

### Let's create the AboutView

- Add the following code in views file **django-project/darna/blog/views.py**

```python
from django.shortcuts import render
from django.views.generic import (TemplateView)

class AboutView(TemplateView):
    template_name = 'about.html'
```

- Create the base template file **django-project/darna/blog/templates/blog/base.html**

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Darna</title>
  </head>
  <body>
    <div class="blog_posts">
      {% raw %} {% block content %} {% endblock %} {% endraw %}
    </div>
  </body>
</html>
```

- Create this file **django-project/darna/blog/templates/blog/about.html**

```html
{% raw %}{% extends "blog/base.html" %} {% block content %}
<h1>About</h1>
<p>Darna is a blogging app powered by Django!</p>
{% endblock %} {% endraw %}
```

- Update the url file of the entire site **django-project/darna/darna/urls.py**

```python
from django.contrib import admin
from django.urls import include, path  # import include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('blog/', include('blog.urls')), # add this line
]
```

- Update the url file of the blog app **django-project/darna/blog/urls.py**

```python
from django.urls import path
from . import views

urlpatterns = [
    path('about/', views.AboutView.as_view()),
]
```

- After completing the above steps, we should have this About page now.
<figure>
   <img src="{{ site.url }}{{ site.baseurl }}/assets/images/django-about-view.png">
   <figcaption>About Page using django Class-based view (CBV)</figcaption>
</figure>
