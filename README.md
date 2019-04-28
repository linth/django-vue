# django-vue
Combine with frontend (Vue.js) and backend (Django) and CRUD by using the rest-framework.

## Usage
```
$ git clone https://github.com/linth/django-vue.git
$ cd django-vue/frontend
$ npm install
$ npm run build

cd ..
$ pip install -r requirent.txt
$ python manage.py makemigrations
$ python manage.py migrate
$ python manage.py runserver
```


## How to create a new django and vue
1. Install django packages
```
$ pip install django==2
$ pip install django-cors-headers
```

2. Create a django project and application.
```
$ django-admin startproject django_vue
$ cd django_vue
$ python manage.py startapp backend
```

3. Edit settings.py in the django project.
```
# settings.py
INSTALLED_APPS = [
    ...
    ...
    'backend',
]
MIDDLEWARE = [
    ...
    ...
    'corsheaders.middleware.CorsMiddleware',
]
TEMPLATES = [
    {
        ...
        'DIRS': ['frontend/dist'],
        ...
    },
]
STATICFILES_DIRS = [
    os.path.join(BASE_DIR, "frontend/dist/static"),
]
CORS_ORIGIN_ALLOW_ALL = True
```

4. Edit the urls.py in the django project.
```
# urls.py
from django.views.generic import TemplateView
urlpatterns = [
    path('admin/', admin.site.urls),
    path('', TemplateView.as_view(template_name='index.html')),
]
```

5. Create a new Vue project.
```
$ vue-init webpack frontend
$ cd frontend
$ npm install
$ npm run build
```

6. Run server
```
$ python manage.py runserver
```
