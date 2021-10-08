# Simple 3 Tier Contact Form App

### Prerequsites:
* Python 3.8 installed
* IDE / Text Editor of your choosing
* Terminal / Command Prompt / Powershell
* Postgre instance (am using 13.3)

### To install:
* Download this repository and navigate to the downloaded project folder within your terminal of choice.

* If using AWS EC2 the following commands will help get started first (not needed when developing locally):
``` bash
sudo apt-get update && sudo yum install libpq-dev python-dev && sudo yum install postgresql-devel && sudo install git && sudo pip install psycopg2
```

* Create a virtual environment within your project folder (Mac you'll need to use python3 instead of python):
``` bash
python -m venv venv

source ./venv/bin/activate
// OR 
.\venv\Scripts\activate
```

* Install any extra dependancies (note again Mac you'll need to use pip3 instead):
``` bash
pip install -r requirements.txt
```

* Provision the database tables within your Postgres instance by running the following within your SQL editor:
``` bash
CREATE TABLE public.contacts
(
    "contactID" SERIAL,
    "fName" character varying(30) COLLATE pg_catalog."default" NOT NULL,
    "lName" character varying(30) COLLATE pg_catalog."default",
    "mName" character varying(30) COLLATE pg_catalog."default",
    "workCompany" character varying(50) COLLATE pg_catalog."default",
    mobile character varying(20) COLLATE pg_catalog."default",
    "homePhone" character varying(20) COLLATE pg_catalog."default",
    "workPhone" character varying(20) COLLATE pg_catalog."default",
    email character varying(50) COLLATE pg_catalog."default",
    "jobTitle" character varying(50) COLLATE pg_catalog."default",
    CONSTRAINT contacts_pkey PRIMARY KEY ("contactID")
)
```

* Within app.py update the following string (on line 7) with your postgres database details:
``` bash
app.config["SQLALCHEMY_DATABASE_URI"] = "postgresql://_YOUR_DB_USER_:_YOUR_DB_URL_:5432/_YOUR_DB_NAME_"
```

### Now you can run locally
* Run the following command in terminal to deploy locally on your computer (python3 on Mac): 
``` bash
python wsgi.py
```

* Or on a server...
``` bash
gunicorn --bind 0.0.0.0:8080 wsgi:app
```
