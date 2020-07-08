# django-docker-tutorial
Tutorial for Django

1. Install docker for your machine.
2. Create a working directory for your Django project, copy the Dockerfile, docker-compose.yml and requirements.txt into that directory.
3. Run (prefix with sudo if using Linux - if necessary) 
```
docker-compose run web django-admin startproject myproject .
```
4. If using Linux, also run
```
sudo chown -R $USER:$USER .
```
5. Edit myproject/settings.py, replace the DATABASE section with:
```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'postgres',
        'USER': 'postgres',
        'PASSWORD': 'postgres',
        'HOST': 'db',
        'PORT': 5432,
    }
}
``` 
6. Run docker-compose up to start the environment
7. Manage/create the files using your native editor e.g. code myproject
8. Run python commands using
```
docker exec -it django_web_1 bash
```
9. Access the web server using http://localhost:8000
10. To access the built-in admin functionality:
```
docker exec django_web_1 ./manage.py migrate
docker exec -it django_web_1 ./manage.py createsuperuser
- create a user e.g. admin, email admin@admin.com, password admin
- type 'y' to bypass password security check if required
- open http://localhost:8000/admin and log in with admin/admin
```
