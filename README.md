# Hosting_to_local


Procedure d'installation d'une application django sur server . mon trojet a pour non test


En supposant qu'on par sur un nouveau server suivre les étapes suivantes:

1- Phase 1

~$ sudo apt-get update
~$ sudo apt-get install python3-pip python3-dev libpq-dev postgresql postgresql-contrib

2- 

~$ git clone test.git
~$ sudo apt install virtualenv
$ virtualenv env -p python3
$ source env/bin/activate
(env) ~/$ cd test
(env) ~/$ pip install -r disquaire/requirements.txt

~$ sudo -u postgres psql
psql (9.5.8)
Type "help" for help.
postgres=# CREATE DATABASE test;
CREATE DATABASE

postgres=# CREATE USER testuser WITH PASSWORD 'mypassword';
CREATE ROLE

postgres=# ALTER ROLE testuser SET client_encoding TO 'utf8';
ALTER ROLE
postgres=# ALTER ROLE testuser SET default_transaction_isolation TO 'read committed';
ALTER ROLE
postgres=# ALTER ROLE testuser SET timezone TO 'Europe/Paris';
ALTER ROLE
postgres=# GRANT ALL PRIVILEGES ON DATABASE test TO testuser;
GRANT


### Dans le settings : configuratiopn de la base de données

settings.py

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'test',
        'USER': 'testuser',
        'PASSWORD': 'mypassword',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}


### Cpnfoguration static & media

Pass debug = False 
