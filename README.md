# Basic-Django-App-Deploying-using-Docker-on-VS-Code

## Basic Django App Deploying using Docker, creating a Docker image, containerize on Docker using VS Code Standalone

## _Successfully created Docker Container image._ 
_Have not share it on IBM Cloud Code Engine_

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

## Test the Server run on http://127.0.0.1:8000
!(https://github.com/eldoma/Basic-Django-App-Deploying-using-Docker-on-VS-Code/blob/main/Docker1.jpg)

### after adding Views, test the HTTPResponse returned by first view on http://127.0.0.1:8000/firstapp 
!(https://github.com/eldoma/Basic-Django-App-Deploying-using-Docker-on-VS-Code/blob/main/firstapp.jpg)

### after adding /date route, test the HTTPResponse returned on http://127.0.0.1:8000/firstapp/date 
!(https://github.com/eldoma/Basic-Django-App-Deploying-using-Docker-on-VS-Code/blob/main/date.jpg)

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
test the HTTPResponse returned by Docker Build on http://127.0.0.1:8000/firstapp 
!(https://github.com/eldoma/Basic-Django-App-Deploying-using-Docker-on-VS-Code/blob/main/firstapp.jpg)

test the HTTPResponse returned by Docker Build on http://127.0.0.1:8000/firstapp/date 
!(https://github.com/eldoma/Basic-Django-App-Deploying-using-Docker-on-VS-Code/blob/main/date.jpg)

### Docker image on Standalone
https://github.com/eldoma/Basic-Django-App-Deploying-using-Docker-on-VS-Code/blob/main/Docker1.jpg

## Attempt to share on IBM Cloud Code Engine 
- $env:APP_NAME = "my-django-app"          
- $env:REGISTRY = "us.icr.io"
- docker tag my-django-app:latest us.icr.io/my_namespace/my-django-app:latest    
- docker push us.icr.io/my_namespace/my-django-app:latest
!(https://github.com/eldoma/Basic-Django-App-Deploying-using-Docker-on-VS-Code/blob/main/Docker2.jpg)       

## _Note: Not successful yet sharing on IBM Cloud Code Engine_
