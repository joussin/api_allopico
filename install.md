
su stephane

cd /home/stephane/

git clone git@github.com:joussin/api_allopico.git

composer update

cp .env.example .env
php artisan key:generate

as root ?

chmod -R 777 /var/www/html/storage/logs
chmod -R 777 /var/www/html/storage/app
chmod -R 777 /var/www/html/storage/framework



## Test

Launch server
``` bash
docker-compose up --build -d
```

SWAGGER
``` bash
open http://127.0.0.1:4444/api/docs/index.html
```


## kill serve

> lsof -i :4444
to check if the port is busy or not if any process is listening to the port 4444 it will be displayed with port id

> sudo  kill -9 [PID]


