---
page_type: sample
languages:
- python
products:
- azure
description: "This repo contains tested reference examples of using Django with SQL Servers."
urlFragment: mssql-django-samples
---


# Django SQL Driver - mssql-django

## Get started

### Windows  
Connect to SQL Database from Django app:
1. **Download Python installer**.  
  Install Python3 if your machine does not have it. Visit [Python download page](https://www.python.org/downloads/windows/).
2. **Install and verify Python**.  
   a. Double click the installer, follow instructions on the screen.  
   b. After finished install. Run `py -V` in command line to verify it. 
```
> py -V
Python 3.7.8 
```
1. **Install django and mssql-django**  
  Use pip to install mssql-django, 
```
> py -m pip install django mssql-django
```
  
### Linux
Connect to SQL Database from Django app:  
1. [**Install Microsoft ODBC Driver for SQL Server on Linux**](https://docs.microsoft.com/en-us/sql/connect/odbc/download-odbc-driver-for-sql-server?view=sql-server-ver15)

2. **Install Python3**
```
# eg. For Ubuntu

$ sudo apt-get install python3
```
3. **Install django and mssql-django**
```
$ python3 -m pip install django mssql-django
```

## Creating a project
1. **Create a Django project**
```
$ django-admin startproject mysite
```
2. **Edit `setting.py` file**  
Go to mysite/mysite/settings.py  
In `DATABASE` section, edit accrodingly. Make sure the `DATABASE_NAME` is exist in your SQL Server instance.
```python
# settings.py
DATABASES = {
    "default": {
        "ENGINE": "mssql",
        "NAME": "DATABASE_NAME",
        "USER": "USER_NAME",
        "PASSWORD": "PASSWORD",
        "HOST": "HOST_ADDRESS",
        "PORT": "1433",
        "OPTIONS": {"driver": "ODBC Driver 17 for SQL Server", 
        },
    },
}

# OR If you want to connect Django's local development with local SQL server instance using Windows Authentication, You may use this configuration
# Leave the `USER`, `PASSWORD` and `PORT` field blank.

DATABASES = {
    'default': {
        'ENGINE': 'mssql',
        'NAME': 'DATABASE_NAME',
        'USER': '',
        'PASSWORD': '',
        'HOST': 'HOST_ADDRESS',
        'PORT': '',
        'TrustedConnection': 'True',
        'OPTIONS': {
            'driver': 'ODBC Driver 17 for SQL Server'
        }
    }
}
 ```
3. **Run Django project**
```
# Linux
$ python manage.py runserver

# Windows
\> py manage.py runserver
```

```
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).

April 22, 2021 - 17:48:06
Django version 3.1.8, using settings 'mysite.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```
Now the development server is running at http://127.0.0.1:8000/. Open browser and navigate to that page, you should be able to see a Django welcome page. 
  
---

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
