# Django Starter Guide

Below is a handy reference to getting your Django Project up and running quickly

# In your terminal 
Navigate to where you want to start your project

    $ cd <name_of_dir>
Create virtual environment

    $ poetry init
        - answer questions
        - Define main Dependencies = YES
        - type django and hit ENTER
        - choose [0] for django
        - enter 
        - django
        - ENTER to confirm generation

Install Poetry Project

    $ poetry install
   
Launch Poetry Shell to configure New Django Project

    $ poetry install
With Django Installed, create Django Project HERE and then you will have access to the manage.py module. **Remember the ' . '** 

    $ django-admin startproject <NameOfProject> . 
> Now that you have created your Django Project, you can call the manage.py functions

Next create the App(s) that you want to for your Django Project. <Name_of_app> this is the name of the app. This will create folder in the Project for the APP (models/views/etc). You can do this as many times as you need to for different apps within your Django Project

    $ python manage.py startapp <NameOfApp>

Next is your initial data migration. This takes the base Django config and creates the basic tables in your DB

    $ python manage.py migrate

Once your basic DB Tables have been constructed, this command will allow you to create a ‘super_user’ aka an admin level user. Good idea to do this now.

    $ python manage.py createsuperuser

This command will launch your project in VSCode

    $ code .

This command will spin up a local dev server. This will allow you access the admin panel @ localhost:8000/admin and to see your project @ localhost:8000

    $ python manage.py runserver

  

# First orders of business:

  

> In Name_Of_Project/settings.py

Go to INSTALLED_APPS and add the name of your app(s) as a string to this list

> this will link up your app(s) to the Django Project

    INSTALLED_APPS  = [
    'name_of_your_app',
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    ]

Go to TEMPLATES[‘DIRS’] and add [BASE_DIR / ‘templates’]

    TEMPLATES  = [
	    {
		    .....
		    'DIRS': [ BASE_DIR  /  'templates'],
    
	    },
    
    ]


Then go ahead and create a folder called ‘templates’ at the root level of your project
```
project  
└───Django_Project
│   │   asgi.py
│   │   settings.py
│   │   urls.py
│   │   wsgi.py.py
│   
└───Django_App
|   │   models.py
|   │   views.py
|   |   admin.py
│   README.md
└───templates
	
```

> This tells Django to look at the root (BASE_DIR) for a folder called
> ‘templates’ when DJANGO is looking for your HTML Templates when a VIEW is called

  

In Name_Of_Project/urls.py

> Declare this import statement at the top

    From <name_of_app>.views import index

> insert this into the url patterns list above admin, name param optional

    
    urlpatterns = [
		    path(‘’, index, name=“homepage”),
		    path('admin/', admin.site.urls),
		    ]

# This is the basic set up
