FROM python:3
RUN mkdir /code
WORKDIR /code
COPY requirements/requirements-common.txt /code/
COPY requirements/requirements-codeserver.txt /code/
RUN pip install -r requirements-common.txt
RUN pip install -r requirements-codeserver.txt
COPY . /code/

#RUN python manage.py makemigrations yaksh
#RUN python manage.py migrate yaksh
#CMD python manage.py runserver 0.0.0.0:8080