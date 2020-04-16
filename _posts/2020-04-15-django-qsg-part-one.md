---
title: 'Django Project - Quickstart Guide Part 1'
date: 2020-04-15T15:30:30-04:00
last_modified_at: 2020-04-16T10:50:02-05:00
categories:
  - Quickstart Guide
tags:
  - QSG
  - Django
---

It has been a long time since I created an app using the Django framework. I want to brush up on it, so I'll create a Django project, and on this post, I'll be taking notes as I go along with the project.

The project that I'll create is a simple blogging app named Darna.

**Notes:** This is not a tutorial, this is just a guide for a general flow when I create a django project and this could change depending on what I feel comfortable to do.
{: .notice--warning}

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

<figure>
    <a href="https://leizleho.com/blog/assets/images/django-basic-setup.png"><img src="https://leizleho.com/blog/assets/images/django-basic-setup.png"></a>
    <figcaption>Viewing the site by navigating to http://127.0.0.1:8000/ in local web browser</figcaption>
</figure>

That's all for the project setup. Let's start writing the code for blogging app!

## Start Coding

- Create models using file **django-project/darna/blog/models.py**
- Create forms using file **django-project/darna/blog/forms.py**
- In blog folder create a folder named "static" for css and javascript files
- Under static folder, create two folder named "css" and "js"
- At the same level of static folder, create another folder called "templates"
- Under templates folder, create folders named "blog" and "registration"

```bash
# blog directory should look like this:
/blog
   /migrations
   /static
      /css
      /js
   /templates
      /blog
      /registration
   __init__.py
   admin.py
   apps.py
   forms.py
   ...
```

- Update the settings file **django-project/darna/darna/settings.py** with the folders just created above
- Find the STATIC_URL and add STATIC_ROOT after it.

```python
STATIC_URL = '/static/'
STATIC_ROOT = os.path.join(BASE_DIR, 'static')  # add this line
```

- For templates folder, find the BASE_DIR and add TEMPLATE_DIR after it

```python
BASE_DIR = os.path.dirname(os.path.dirname(os.path.abspath(__file__)))
TEMPLATE_DIR = os.path.join(BASE_DIR,'blog/templates/blog') # add this line
```

- Let's also add the LOGIN_REDIRECT_URL after the STATIC_ROOT

```python
STATIC_URL = '/static/'
STATIC_ROOT = os.path.join(BASE_DIR, 'static')

LOGIN_REDIRECT_URL = '/'  # add this line
```

# Summary

In this post, we setup a django project, added models and forms, and configured settings for installed apps, templates directory and static directory.
