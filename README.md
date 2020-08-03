# Prometheus Json Exporter

```
$ docker-compose up -d
```

open brower

http://127.0.0.1:3000

default username=admin, password=admin

change your password

Go to Configuration->Datasource

add Prometheus datasource with URL = http://prometheus:9090

then you will find all metric we defined in

`json_exporter/json` folder