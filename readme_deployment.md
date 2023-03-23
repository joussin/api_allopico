
# deployment steps

### as root 

docker-compose down


### as stephane

su stephane

cd /home/stephane/

git clone git@github.com:joussin/api_allopico.git

cd api_allopico

### as root

su root

docker-compose up --build -d

docker exec -it api_picolo_php_container bash

### as stephane

su stephane

composer update

cp .env.example .env
php artisan key:generate

chmod -R 777 /var/www/html/storage/logs
chmod -R 777 /var/www/html/storage/app
chmod -R 777 /var/www/html/storage/framework



``` bash
open http://jouss.in/
```

---

## Local

Launch server
``` bash
docker-compose up --build -d
```

SWAGGER
``` bash
open http://127.0.0.1:4444/
```
