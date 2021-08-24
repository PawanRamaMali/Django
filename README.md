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

* [What is Django](#what-is-Django-?)
* URLs, Routes and Views
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
