# Django_tutorial

## Requirement
- python latest version [Python](https://www.python.org/)
- git latest version [Git](https://git-scm.com/)
### Install python package
```
$ pip install django
```
Check if Django installed already.
```
$ python -m django --version
3.0.7
```
### Creating a project
```
django-admin startproject django_tutorial
```
### Creating the Polls app
```
python manage.py startapp polls
```
### Write your first view
**polls/views.py**
```python
from django.http import HttpResponse


def index(request):
    return HttpResponse("Hello, world. You're at the polls index.")
```
**polls/urls.py**
```python
from django.urls import path

from . import views

urlpatterns = [
    path('', views.index, name='index'),
]

```