---
title: 'Django Project - Quickstart Guide Part 1'
date: 2020-04-15T15:30:30-04:00
categories:
  - Quickstart Guide
tags:
  - QSG
---

It has been a long time since I created an app using the Django framework. I want to brush up on it, so I'll create a Django project, and on this post, I'll be taking notes as I go along with the project.

The project that I'll create is a simple blogging app named Darna.

## Creating the project

```bash
# Setup environment
mkdir django-project
cd django-project
python3 -m venv env

# Activate the environment
source ./env/bin/activate

# Install django
pip install django

# Create the new project using the `django-admin startproject` command
django-admin startproject darna
cd darna
```

## Creating the application

```bash
# This must be run in the same folder as the project's manage.py
python manage.py startapp blog
touch ./blog/urls.py
touch ./blog/forms.py
```

## Registering the blog application

Open the project settings file **django-project/darna/darna/settings.py** and find the definition for the INSTALLED_APPS list. Then add the `blog` at the end of the list.

```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'blog',
]
```

## Testing the site

```bash
python manage.py makemigrations blog
python manage.py migrate
python manage.py runserver
```

Viewing the site by navigating to http://127.0.0.1:8000/ in local web browser

<figure>
    <a href="https://leizleho.com/blog/assets/images/django-basic-setup.png"><img src="https://leizleho.com/blog/assets/images/django-basic-setup.png"></a>
    <figcaption>Viewing the site by navigating to http://127.0.0.1:8000/ in local web browser</figcaption>
</figure>

That's all for the project setup. Let's start writing the code for blogging app!
