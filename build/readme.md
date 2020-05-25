## How to build


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

copy the settings file

```

```


4. run the docker-compose file

```
sudo docker-compose up -d
```


5. login the dijango web and run the below commands

```
sudo docker exec -it online_test-0201_web_1 bash
python manage.py makemigrations yaksh
python manage.py migrate
python manage.py createsuperuser
```

6. open the browser

http://localhost:8080
