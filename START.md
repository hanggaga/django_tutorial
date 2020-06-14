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
## Writing your first Django app, part 1
### Creating a project
```
django-admin startproject django_tutorial
```
### The development server
```
$ python manage.py runserver
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
**django_tutorial/urls.py**
```python
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path('polls/', include('polls.urls')),
    path('admin/', admin.site.urls),
]
```
## Writing your first Django app, part 2
### Database setup
#### Install MySQL
```
$ pip install PyMySQL
```
**django_tutorial/settings.py**
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'hmc_python',
        'USER': 'admin_hmc_python',
        'PASSWORD': '(!&#@Humani@a2019',
        # Or an IP Address that your DB is hosted on
        'HOST': 'smartdoc.mysql.singapore.rds.aliyuncs.com',
        'PORT': '3306',
        'OPTIONS': {
            'init_command': "SET sql_mode='STRICT_TRANS_TABLES', innodb_strict_mode=1",
        }
    }
}
```
**django_tutorial/\_\_init\_\_.py**
```python
import pymysql

pymysql.version_info = (1, 3, 13, "final", 0)
pymysql.install_as_MySQLdb()
```