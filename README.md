# dockersqlserver

<img src="https://user-images.githubusercontent.com/45560312/128073753-3c84a85e-8de4-4693-97ac-3cc462a18547.png" width="60" height="50">
<img src="https://user-images.githubusercontent.com/45560312/130338832-9a221ab5-cd4b-4194-87a2-4974e6400443.png" width="60" height="50">

##### this image is for anyone who wants to use their Microsoft SQL Server using a FreeTDS driver with the latest version of python installed.

https://github.com/adgsenpai/dockersqlserver/pkgs/container/dockersqlserver

# Usage in your IMAGE

#### Dockerfile

```
FROM ghcr.io/adgsenpai/dockersqlserver:main

COPY . .

RUN MyApp.py
```

#### MyApp.py

Using Native PyODBC in Image

```
import pyodbc

conn = pyodbc.connect('DRIVER=FreeTDS;SERVER=<IP_OR_HOSTNAME>;PORT=1433;DATABASE=<DATABASE_NAME>;UID=<USERNAME>;PWD=<PASSWORD>;TDS_Version=8.0;')
cursor = conn.cursor()
for row in cursor.execute('select 6 * 7 as [Result];'):
    print row.Result
```

Using my module included in Image

```
import sqlserver

db = sqlserver.adgsqlserver(
    'DRIVER=FreeTDS;SERVER=<IP_OR_HOSTNAME>;PORT=1433;DATABASE=<DATABASE_NAME>;UID=<USERNAME>;PWD=<PASSWORD>;TDS_Version=8.0;')
    
print(db.ReturnRecordsAsDict('select 6 * 7 as [Result];'))
```


##### ADGSTUDIOS 2021
