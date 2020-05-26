## How to build the docker image


1. Download yaksh code

```
wget https://github.com/FOSSEE/online_test/archive/v0.20.1.tar.gz
tar xvzf v0.20.1.tar.gz
```

2. copy files

```
cp Dockerfile online_test-0.20.1/.
```

3. Edit dijango settings file


vi online_test/settings.py

```
change ALLOWED_HOSTS = ['*']

comment out  :

MIDDLEWARE
#    'yaksh.middleware.get_notifications.NotificationMiddleware',

```

DB changes
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


(or)

copy the settings file from this folder


5.  build and push the image

```
sudo make build
sudo make push

```

## How to deploy 

1. create a folder 

```
mkdir yaksh
cd yaksh
``` 

2. run the docker-compose file from this folder

```
sudo docker-compose up -d
```


3. login the dijango web container and run the below commands

```
sudo docker exec -it online_test-0201_web_1 bash
python manage.py makemigrations 
python manage.py makemigrations notifications_plugin
python manage.py migrate
python manage.py loaddata demo_fixtures.json
```

default users (admin/admin, teacher/teacher, student/student) are created

4. open the browser

http://localhost:8080

