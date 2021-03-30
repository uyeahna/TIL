## ORM

```bash

YN@DESKTOP-YENA MINGW64 ~/SSAFY5/exercise/django/0325/99_sql_orm/sql_orm
$ python -m venv vevn

YN@DESKTOP-YENA MINGW64 ~/SSAFY5/exercise/django/0325/99_sql_orm/sql_orm
$ source vevn/Scripts/activate
(vevn) 
YN@DESKTOP-YENA MINGW64 ~/SSAFY5/exercise/django/0325/99_sql_orm/sql_orm
$ pip list
Package    Version
---------- -------
pip        20.2.3 
setuptools 49.2.1 
WARNING: You are using pip version 20.2.3; however, version 21.0.1 is available.
You should consider upgrading via the 'c:\users\yn\ssafy5\exercise\django\0325\99_sql_orm\sql_orm\vevn\scripts\python.exe -m pip install --upgrade pip' command.    
(vevn) 
YN@DESKTOP-YENA MINGW64 ~/SSAFY5/exercise/django/0325/99_sql_orm/sql_orm
$ pip install -r requirements.txt
....
WARNING: You are using pip version 20.2.3; however, version 21.0.1 is available.
You should consider upgrading via the 'c:\users\yn\ssafy5\exercise\django\0325\99_sql_orm\sql_orm\vevn\scripts\python.exe -m pip install --upgrade pip' command.    
(vevn) 
YN@DESKTOP-YENA MINGW64 ~/SSAFY5/exercise/django/0325/99_sql_orm/sql_orm
$ python manage.py migrate
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions, users
Running migrations:
  Applying contenttypes.0001_initial... OK
...
(vevn) 
YN@DESKTOP-YENA MINGW64 ~/SSAFY5/exercise/django/0325/99_sql_orm/sql_orm
$ python manage.py sqlmigrate users 0001
BEGIN;
--
-- Create model User
--
CREATE TABLE "users_user" ("id" integer NOT NULL PRIMARY KEY AUTOINCREMENT, "first_name" varchar(10) NOT NULL, "last_name" varchar(10) NOT NULL, "age" integer NOT NULL, "country" varchar(10) NOT NULL, "phone" varchar(15) NOT NULL, "balance" integer NOT NULL);
COMMIT;
(vevn)

YN@DESKTOP-YENA MINGW64 ~/SSAFY5/exercise/django/0325/99_sql_orm/sql_orm
$ ls
db.sqlite3  manage.py  my_sql  requirements.txt  users  users.csv  venv

YN@DESKTOP-YENA MINGW64 ~/SSAFY5/exercise/django/0325/99_sql_orm/sql_orm
$ sqlite3 db.sqlite3
SQLite version 3.35.2 2021-03-17 19:07:21
Enter ".help" for usage hints.
sqlite> .tables
auth_group                  django_admin_log
auth_group_permissions      django_content_type
auth_permission             django_migrations
auth_user                   django_session
auth_user_groups            users_user
auth_user_user_permissions
sqlite> .mode csv
sqlite> .import users.csv users_user
users.csv:1: INSERT failed: datatype mismatch
sqlite> SELECT * FROM users_user;
1,"정호","유",40,"전라북도",016-7280-2855,370
2,"경희","이",36,"경상남도",011-9854-5133,5900
3,"정자","구",37,"전라남도",011-4177-8170,3100
...
sqlite> .schema users_user
CREATE TABLE IF NOT EXISTS "users_user" ("id" integer NOT NULL PRIMARY KEY AUTOINCREMENT, "first_name" varchar(10) NOT NULL, "last_name" varchar(10) NOT NULL, "age" integer NOT NULL, "country" varchar(10) NOT NULL, "phone" varchar(15) NOT NULL, "balance" integer NOT NULL);


```

```python
창하나더켜서

YN@DESKTOP-YENA MINGW64 ~/SSAFY5/exercise/django/0325/99_sql_orm/sql_orm
$ source venv/s
Scripts/ share/

YN@DESKTOP-YENA MINGW64 ~/SSAFY5/exercise/django/0325/99_sql_orm/sql_orm
$ source venv/Scripts/activate
(vevn)
YN@DESKTOP-YENA MINGW64 ~/SSAFY5/exercise/django/0325/99_sql_orm/sql_orm
$ python manage.py shell_plus
# Shell Plus Model Imports
from django.contrib.admin.models import LogEntry
from django.contrib.auth.models import Group, Permission
from users.models import User
from django.contrib.contenttypes.models import ContentType
from django.contrib.sessions.models import Session
# Shell Plus Django Imports
from django.core.cache import cache
from django.conf import settings
from django.contrib.auth import get_user_model
from django.db import transaction
from django.db.models import Avg, Case, Count, F, Max, Min, Prefetch, Q, Sum, When
from django.utils import timezone
from django.urls import reverse
from django.db.models import Exists, OuterRef, Subquery
C:\Users\YN\AppData\Local\Programs\Python\Python38\lib\site-packages\IPython\core\interactiveshell.py:936: UserWarning: Attempting to work in a virtualenv. If you encounter problems, please install IPython inside the virtualenv.
  warn("Attempting to work in a virtualenv. If you encounter problems, please "
Python 3.8.7 (tags/v3.8.7:6503f05, Dec 21 2020, 17:59:51) [MSC v.1928 64 bit (AMD64)]
Type 'copyright', 'credits' or 'license' for more information        
IPython 7.19.0 -- An enhanced Interactive Python. Type '?' for help. 

In [2]: User.objects.all()
Out[2]: <QuerySet [<User: User object (1)>, <User: User object (2)>, 
<User: User object (3)>, <User: User object (4)>, <User: User object 
(5)>, <User: User object (6)>, <User: User object (7)>, <User: User object (8)>, <User: User object (9)>, <User: User object (10)>, <User: User object (11)>, <User: User object (12)>, <User: User object (13)>, <User: User object (14)>, <User: User object (15)>, <User: User object (16)>, <User: User object (17)>, <User: User object (18)>, <User: User object (19)>, <User: User object (20)>, '...(remaining elements truncated)...']>

In [3]: User.objects.create(last_name="홍", first_name="길동", age=1 
   ...: 8, country='hanyang', phone='123-4567-8901', balance=20000)  
Out[3]: <User: User object (101)>

In [4]: User.objects.get(id=101)
Out[4]: <User: User object (101)>

In [5]: user = User.objects.get(pk=101)
   ...: user.last_name = '김'
   ...: user.save()

In [6]: user = User.objects.get(pk=101)
   ...: user.delete()
   ...: 
Out[6]: (1, {'users.User': 1})

In [7]: exit()
(vevn) 

YN@DESKTOP-YENA MINGW64 ~/SSAFY5/exercise/django/0325/99_sql_orm/sql_orm
$ python manage.py shell_plus --print-sql
       
In [1]: User.objects.count()
SELECT COUNT(*) AS "__count"
  FROM "users_user"

Execution time: 0.000000s [Database: default]
Out[1]: 101
       
In [3]: User.objects.filter(age=30).values('first_name')
Out[3]: SELECT "users_user"."first_name"
  FROM "users_user"
 WHERE "users_user"."age" = 30
 LIMIT 21

Execution time: 0.000998s [Database: default]
<QuerySet [{'first_name': '영환'}, {'first_name': '보람'}, {'first_name': '은영'}]>

       
```

