# Simple 3 Tier Contact Form App

### Prerequsites:
* Python 3.8 installed
* IDE / Text Editor of your choosing
* Terminal / Command Prompt / Powershell

### To install:
* Download this repository and navigate to the downloaded project folder within your terminal of choice.
* Create a virtual environment within your project folder (note some systems you'll need to use python3 instead):
``` bash
python -m venv venv
.\venv\Scripts\activate
```
* Install any extra dependancies (note again some systems you'll need to use pip3 instead):
``` bash
pip install -r requirements.txt
```

* Within app.py update the following string (on line 7) with your postgres database details:
``` bash
app.config["SQLALCHEMY_DATABASE_URI"] = "postgresql://_YOUR_DB_USER_:_YOUR_DB_URL_:5432/_YOUR_DB_NAME_"
```

### Now you can run locally
* Run the following command in terminal to deploy locally on your computer: 
``` bash
python wsgi.py
```

* Or on a server...
``` bash
gunicorn --bind 0.0.0.0:8080 wsgi:app
```
