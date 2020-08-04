# Prometheus Json Exporter


## 1. Use it separately

### build docker image 

```
$ cd json_exporter
$ docker build -t prometheus_json_exporter .
$ docker image ls
REPOSITORY                                       TAG                 IMAGE ID            CREATED             SIZE
prometheus_json_exporter                         latest              181892e1075d        16 hours ago        92 MB
``` 

### prepare the json metric files

example format can be found in `json_exporter/json`

```
$ tree json/
json/
├── metric1.json
└── metric2.json

0 directories, 2 files
```

### start the container


```
$ ls
json
$ docker run -d -p 5000:5000 -v $(pwd):/root/json prometheus_json_exporter
eeac202d600a3c630cfbb982b4fb3765ce74f04e9c1a0062bfe834fb8660452f
$ docker ps
CONTAINER ID        IMAGE                                                   COMMAND                  CREATED             STATUS              PORTS                                                   NAMES
eeac202d600a        prometheus_json_exporter                                "./run_server.sh"        3 seconds ago       Up 2 seconds        0.0.0.0:5000->5000/tcp                                  stupefied_spence
```

### scrape the metric


```
$ curl 127.0.0.1:5000/metrics
```


## 2. Use it with docker compose


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
