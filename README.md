# Photo Quality Recommendations (2022)

[English](README.md) | [Русский](README.ru.md)

A Django application that reviews reportage photos and gives recommendations based on image analysis.

## Features

- User registration and Google sign-in.
- A personal account for uploaded photos.
- Photo uploads with shooting parameters.
- Analysis of light and shadow, composition, histograms, and contours.
- Recommendations based on the analysis results.

## Tech stack

Python, Django, OpenCV, Matplotlib, NumPy, SQLite, and django-allauth for Google sign-in. The settings were created with Django 4.0.4.

## Project structure

- `app/` — models, views, forms, migrations, and image analysis.
- `core/` — Django settings and URL configuration.
- `templates/` — account and photo pages.
- `static/` — styles and images.
- `env.example` — local configuration template.

## Local configuration

From the project root, copy the template and generate a new Django key:

```bash
cp env.example .env
python -c "import secrets; print(secrets.token_urlsafe(50))"
```
Put the generated value in `DJANGO_SECRET_KEY` in `.env`. For Google sign-in, enter your own application's credentials in the `GOOGLE_*` variables. Both settings files read these values from the environment.

After installing the project dependencies, load the environment and create a fresh local database from the migrations:

```bash
set -a
. ./.env
set +a
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```
Open `http://localhost:8000`. Configure the Django Sites entry for your local address when using Google sign-in. The SQLite database is created locally; its contents and `.env` are excluded from Git.
