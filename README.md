# What is Django ?

* Django is Python web development framework 
* Allows us to focus on core business logic
* Batteries included approach : offers build in solutions and features for basically all problems 
* Customizable and extensible 
* Built for Python 3.x 
* Build Production ready websites 

## Prerequisites

* Basic Python knowledge 
* Basic web devlopment knowledge 

### Installing Python & Django

* Python - [Download Link](https://www.python.org/downloads)

* Django - From command prompt run below command. 
 
 ```
 python -m pip install Django
 ```
 
 To verify , run the below command in command prompt 
 
 ```
 django-admin
 ```
 
# Contents

Part I - Foundations

* [What is Django](#what-is-Django-)
* [URLs, Routes and Views](#urls-routes-and-view)
* Templates and Static Files
* Data, Models and relationships

Part II - Advanced

* Working with Forms
* Class based Views
* File Uploads
* Sessions

Part III - Projects

* Small examples
* Building a Blog
* Frontend + Admin Area
* Deployment 


## Using a Virtual Environment

* Virtual environment allows you to install Python modules into the different environments and hence have project-specific modules (instead of global modules).

* You can learn more about virtual environments with Python here: https://docs.python.org/3/tutorial/venv.html

* Using virtual environments is recommended but is not mandatory.

## Using "Pylance"

* When using Visual Studio Code (recommended), you can use the "Pylance" extension to get better code checks and code completion.

* To enable it in your Python / Django project, you can add a special setting to your your project-specific configuration (i.e. your .vscode/settings.json file):

```
{
"python.languageServer": "Pylance",
}
```

## Create a Django Project 
 
```
django-admin startproject mypage
```
Here `mypage` is the name of project

## Create Django Apps

```
python manage.py startapp challenges
```
Here `challenges` is the name of app inside django project



## URLs (Routes) and View


![image](https://user-images.githubusercontent.com/11299574/130835950-b95e2d50-a4fe-40b4-a91c-45cfee0b702e.png)

    * Example of URL - https://github.com/ 
    * Show Profile - https://github.com/PawanRamaMali 
    * View Repositories - https://github.com/PawanRamaMali?tab=repositories 

* URLs > Result : URL action mappings ensure that certain results are achieved when certain URLs are entered by the user. 

* Views are responsible for processing requests (parsing the URL, HTTP method and potential request data) and creating a response
* Views in Django are the logic that is executed for different URLs ( and Http methods)
* Could be a function or class when certain URL is requested 
* Code inside the function / class handles (evaluates) requestes and returns responses
  * Load and prepare data 
  * Run any other business logic
  * Prepare and return response data 


## Functional View Example 
[Back to Contents](#contents)

![image](https://user-images.githubusercontent.com/11299574/130840219-351fdce1-ef3e-4ecd-9578-6063f49733d1.png)

### Adding Views and URLs
[Back to Contents](#contents)

Inside the django app folder, edit the `views.py` file as below 

```py
from django.shortcuts import render # Present by default 
from django.http import HttpResponse # Added for returning the response 

# Create views here. 

def index(request):  # Receive the request 
    return HttpResponse("This works !")  # Return simple string as response

```

In the same directory, create `urls.py` 

```py
from django.urls import path # To use path function
from . import views # import the views.py file functions

urlpatterns = [
    path("january", views.index) # If a request reached the url ~/january , execute index function from views file
]

```

In the project's `urls.py` file 

```py
from django.contrib import admin
from django.urls import path, include # added include to add include function

urlpatters = [
    path('admin/', admin.site.urls),  # default path for admin 
    path('challenges/', include('challenges.urls')) # follow or forward requests to app's url patterns from here
]
```

### Dynamic Path Segments & Captured values
[Back to Contents](#contents)

Inside the django app folder, edit the `views.py` file as below 

```py
from django.shortcuts import render
from django.http import HttpResponse , HttpResponseNotFound # To send 404 error

# Create views here. 

def monthly_challenges(request , month):  # Second argument in urlpatterns
    challenge_text = None
    if month == 'january':
        challenge_text  = "January text example" 
    elif month = 'february':
        challenge_text  = "February text example"
    else:
        return HttpResponseNotFound("This month is not supported")
        
    return HttpResponse(challenge_text)  

```

In the same directory, create `urls.py` 

```py
from django.urls import path 
from . import views 

urlpatterns = [
    path("<month>", views.monthly_challenges) # If a request reached the url with any text , execute monthly_challenges function from views file
]

```
