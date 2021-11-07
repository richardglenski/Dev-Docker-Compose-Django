adapted from:
https://londonappdeveloper.com/deploying-django-with-docker-compose/
https://github.com/LondonAppDeveloper/deploy-django-with-docker-compose


============    Git commands   ============

git init

git add README.md

git commit -m "initial setup commit"

git branch -M main

git remote add origin https://github.com/richardglenski/Dev-Docker-Compose-Django

git push origin main

git pull origin main

git push -u origin main

git remote -v

git branch -M main

git push -u origin main


==========   CREATE    ==============

docker-compose build

docker-compose run --rm app sh -c "django-admin startproject app ."

docker-compose run --rm app sh -c "python manage.py startapp core"

docker-compose run --rm app sh -c "python manage.py makemigrations"

docker-compose up
( ^C )

docker-compose run --rm app sh -c "python manage.py createsuperuser"
adminuser
richardg@fm

docker-compose up
( ^C )

user1
gopasuser1

Proxy:
All configuration values can be set on the server we deploy to by adding a file called .env.

It’s often useful to provide a template of this file with some dummy values that is commited to Git, so we know what values to set when deploying.

Create a new file called .env.sample in the root of the project and add the following contents:

DB_NAME=dbname
DB_USER=rootuser
DB_PASS=changeme
SECRET_KEY=changeme
ALLOWED_HOSTS=127.0.0.1


Now run the following command to test our deployment locally:

docker-compose -f docker-compose-deploy.yml down --volumes
docker-compose -f docker-compose-deploy.yml build
docker-compose -f docker-compose-deploy.yml up
( ^C )

docker-compose -f docker-compose-deploy.yml run --rm app sh -c "python manage.py createsuperuser"

