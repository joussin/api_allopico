
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


