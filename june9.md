June 9 ~ Django ORM
============================

### The Journey of a Web Request in Django

<iframe width="100%" height="500" src="https://www.youtube.com/embed/RLo9RJhbOrQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



### Create a new Django project
In the virtual environment `pip install django`.  If you need a specific version `pip install django==2.0.1`  

-  Create a new Django project with `django-admin startproject project_name`.  This will create a folder for the project with `manage.py`.  I'll refer to this going forward as the `project directory`.  You'll find `settings.py` and `urls.py` in a subdirectory of the project directory.    
-  Next create your first Django application.  Go to the project directory and type `manage.py startapp app_name`.    

<img src="https://raw.githubusercontent.com/HCDigitalScholarship/ds-cookbook/master/google_vision/why-django-for-web-development-8-638.jpg" />


- The migrate command will update the database based on the code in your `models.py` and other files.  To make the db reflect your current code, type `$ python manage.py migrate`.  This will update the db with the tables needed to create users and user groups.  

- Before you can log in to the admin page, you'll need to create a user by typing `$ python manage.py createsuperuser`.    
- To add you new app to the project, edit `settings.py`.  Use a text editor to add `'app_name',` to the INSTALLED_APPS section.  
```python
INSTALLED_APPS = (
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'app_name',
)
```

### URLS 

*urls.py* 
```python
from django.urls import include, path

urlpatterns = [
    path('index/', views.index, name='main-view'),
    path('/goto', views.goto, name='goto'),
    ...
]
```

### Views 

[Function-based view](https://docs.djangoproject.com/en/3.0/topics/http/views/
)

*views.py*
```python
from django.shortcuts import render
from myapp.models import goto

def goto(request):
  context = {}
  context['gotos'] = goto.objects.all()
  return render(request, "goto.html", context)

```

[Class-based view](https://docs.djangoproject.com/en/3.0/topics/class-based-views/intro/)

*views.py*
```python
from django.views.generic.base import TemplateView
from myapp.models import goto

class GoTo(TemplateView):

    template_name = "goto.html"

    def get_context_data(self, **kwargs):
        context = super().get_context_data(**kwargs)
        context['gotos'] = goto.objects.all()
return context
```

### Models 

1. [Django models docs](https://docs.djangoproject.com/en/3.0/topics/db/models/)
2. [Mozilla on Django Models](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Models)
3. [Django ORM](https://docs.djangoproject.com/en/3.0/topics/db/queries/) 

*models.py*
```python
from django.db import models

class goto(models.Model):
    first_name = models.CharField(max_length=30)
    last_name = models.CharField(max_length=30)

    def __str__(self):
        return f"{self.first_name} {self.last_name}"

```

### Adding Data 

Open the project shell.
`$ python manage.py shell`

```python
>>> from myapp.models import goto
>>> new_goto, created = goto.objects.update_or_create(first_name="Andy", last_name="Janco")
>>> print(new_goto.id, new_goto.first_name, new_goto.last_name)
1 Andy Janco

```
See also [loaddata and fixtures](https://docs.djangoproject.com/en/3.0/howto/initial-data/#providing-initial-data-for-models)

### Manage.py commands 

Run a local server
`python manage.py runserver`

Update the db schema based on models.py
`python manage.py makemigrations`
`python manage.py migrate`

[Create models.py from an existing db](https://docs.djangoproject.com/en/3.0/howto/legacy-databases/)
`python manage.py inspectdb > models.py`

You can [create your own commands](https://docs.djangoproject.com/en/3.0/howto/custom-management-commands/) as well

- place a file in `myapp/management/commands`

```python
from django.core.management.base import BaseCommand
import pandas as pd
from pathlib import Path

class Command(BaseCommand):
    help = 'Import new data from a csv file'

    def add_arguments(self, parser):
        parser.add_argument('path', nargs='+', type=int)

    def handle(self, *args, **options):
      path = Path(options['path'])
      df = pd.read_csv(path)
```

### Further Reading

- [Mozilla Django Tutorial](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django)

- [Real Python](https://realpython.com/get-started-with-django-1/)

- [Django Girls](https://tutorial.djangogirls.org/en/django/)

Cookbook entries
- [Flatpages and ckeditor](https://github.com/HCDigitalScholarship/ds-cookbook/tree/master/django_flatpages)
- [Support many languages](https://github.com/HCDigitalScholarship/ds-cookbook/tree/master/internationalization)
- [User registration with confirmation email](https://github.com/HCDigitalScholarship/ds-cookbook/tree/master/django_email_verification)
- [Use Google for user authentication](https://realpython.com/adding-social-authentication-to-django/)
- [Import and Export data in Admin](https://github.com/HCDigitalScholarship/ds-cookbook/tree/master/django-import-export)
- [DataTables: Server Side Processing](https://github.com/HCDigitalScholarship/ds-cookbook/tree/master/datatables-server-side-processing)



## That '70s Database Language

```sql
SELECT people FROM party WHERE groove LIKE 'get Down' OR 'boogie';

```

<img src="https://img1.looper.com/img/gallery/we-finally-understand-why-that-70s-show-was-canceled/intro-1568723982.jpg" width="50%">

` SQL is like Latin for data analysts/scientists. You may not always realize you are using it, but you are probably using it.`



### Relational Database Design

Relational databases are still the most common form of data storage and management, even after all these years. They are essentially a series of tables, linked by common key values. Best practice for database design dictates that each table has a designated _primary key_ field, which acts a unique identifier for a database record.

Tables are linked through _foreign keys_, which match a field and value in one table with the primary key field and value in another table.


Relational databases are built on three types of relationships:

1. One-to-one
2. One-to-many
3. Many-to-many

<img src="er.png">

### SQL 

Most relational databases use some flavor of SQL--structured query language--to query and manage the data.

[w3schools](https://www.w3schools.com/sql/default.asp)

[DigitalOcean: A Basic MySQL Tutorial](https://www.digitalocean.com/community/tutorials/a-basic-mysql-tutorial)

MySQL is one of the most longstanding and popular open-source database engines, with PostgreSQL as its more robust competition. "Postgres" has additional features like geospatial data and querying, which makes data-driven mapping possible. We use both in our projects, as MySQL is easier to use while Postgres's spatial capacity creates new project opportunities for us.

[Why should you care about PostGIS?--A Gentle Introduction to Spatial Databases](https://medium.com/@tjukanov/why-should-you-care-about-postgis-a-gentle-introduction-to-spatial-databases-9eccd26bc42b)

A long time ago, I wrote half a thing about database design principles. [Check it out!](https://docs.google.com/document/d/1TPVSVuMJk2kQ-G2rMBhBLoB5dH5ghQl0_H0IBP6FYIY/edit)


[`python manage.py dbshell`](https://docs.djangoproject.com/en/3.0/ref/django-admin/#dbshell)

[Django Q objects](https://docs.djangoproject.com/en/3.0/topics/db/queries/#complex-lookups-with-q-objects)

[Django postgres search](https://docs.djangoproject.com/en/3.0/ref/contrib/postgres/search/)

https://www.sequelpro.com/

https://www.jetbrains.com/datagrip/

https://dbeaver.io/

