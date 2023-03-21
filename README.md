## Introduction to django allauth with google authentication 
---
![Django allauth providers image](https://images.pexels.com/photos/262367/pexels-photo-262367.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1)

### Steps to set up a django authentication system using the django allauth package

### Setup a django project

### Stop 1: Create Virtual Environment

Create a virtual environment to hold and isolate the project source code on you local machine

```python3.10 -m venv env```

```python3.10``` this is the version of python installed in my case

make sure to check yours first using the command ```python --version```

Activate the virtual env

```source env/bin/activate``` 

Confirm by using the following command on mac/linux

```which python```

your output should be similar to this

```/home/host/path/django_allauth_tutorial/env/bin/python```

### Step 2: Install Project Dependencies

Once the local environment is up and running 
Use the following command to install project dependencies

```pip install django==3.2.0 django-allauth```

Start a new project using the following command

```django-admin startproject django_allauth .```

### Step 3: Configure the project related settings

Once the project is redy go into settings.py file of the main application and add the following

Add the django authentication backends

```AUTHENTICATION_BACKENDS = [
    ...
    # Needed to login by username in Django admin, regardless of `allauth`
    'django.contrib.auth.backends.ModelBackend',

    # `allauth` specific authentication methods, such as login by e-mail
    'allauth.account.auth_backends.AuthenticationBackend',
    ...
]

```
Make sure you have the list of the following apps in you install apps in settings.py 
```
    'django.contrib.auth',
    'django.contrib.messages',
    'django.contrib.sites',

    'allauth',
    'allauth.account',
    'allauth.socialaccount'
```

Add the specific provider you wish to authenticate against in this case (Google) into your installed apps

```'allauth.socialaccount.providers.google'```

http://127.0.0.1:8000/accounts/google/login/callback/

```python manage.py runserver```

Set the site ID in settings.py

```SITE_ID = 1```
Update the main urls.py file you applicatioin to look like this

```urlpatterns = [
    ...
    path('accounts/', include('allauth.urls')),
    ...
]
```
To learn more or if you have any trouble with the steps feel free to visit the documentation right [here](https://django-allauth.readthedocs.io/en/latest/installation.html)

Back to the terminal.

To make mygrations run:

```python manage.py makemigrations```

to migrate:

```python manage.py migrate```

To create a super user so that we can login to the admin and configue the social apps run:

```python manage.py createsuperuser```

Fill in the information nedded 

Log in to the django admin using http://localhost:8000/admin -> by default

Go to soccial apps

[admin page](file:///run/user/1000/gvfs/google-drive:host=gmail.com,user=miclemabasie3/0AGeJ3YJdopk1Uk9PVA/1Foo7R_6k0Jgz-NeNztqLQsdqtWlqJRpZ/1JqEQsp8liG7457GGx6NjtibTGL3EypoM)

