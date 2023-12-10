# Basic-Django-App-Deploying-using-Docker-on-VS-Code

## Basic Django App Deploying using Docker, creating a Docker image, containerize on Docker using VS Code Standalone

_SUccessfully created Docker Container image. Have not share it on IBM Cloud Code Engine_

## Install these must-have packages and setup the Django environment.

- pip install --upgrade distro-info
- python.exe -m pip install --upgrade pip==23.2.1 --user
- pip install virtualenv        
- virtualenv djangoenv replace with python -m venv djangoenv       
- source djangoenv/bin/activate replace with .\djangoenv\Scripts\activate    

## Setup Django related packages & Database Tables Migration
- pip install Django    
- django-admin startproject firstproject  
- python manage.py startapp firstapp     
- python manage.py makemigrations    
- python manage.py migrate   
- python manage.py runserver                                                                                                                                   

## Test the Server run on http://127.0.0.1:8000/

### after adding Views, test the HTTPResponse returned by first view on http://127.0.0.1:8000/firstapp 

### after adding /date route, test the HTTPResponse returned on http://127.0.0.1:8000/firstapp/date 

# Containerize the App using Docker 
## Open new terminal Go to specific project directory
- cd firstapp
- python.exe -m pip install --upgrade pip    
- python.exe -m pip install --force-reinstall pipreqs --user     
- python -m pipreqs.pipreqs .    

### Run the following command to create and run the container image        
- docker build -t my-django-app:latest .    
- docker run -e PYTHONUNBUFFERED=1 -p 8000:8000 my-django-app    

### The result must be the same with the HTTPResponse returned

### Docker image

## Attempt to share on IBM Cloud Code Engine (not successful yet)
- $env:APP_NAME = "my-django-app"          
- $env:REGISTRY = "us.icr.io"
- docker tag my-django-app:latest us.icr.io/my_namespace/my-django-app:latest    
- docker push us.icr.io/my_namespace/my-django-app:latest       
