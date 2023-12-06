# Grafana Custom Docker Image For Data Federation SQL Access

## Build Docker Image

Plain

```
docker build \
  --build-arg "GRAFANA_VERSION=latest-ubuntu" \
  -t grafana-custom .
```

With SQLYZE ODBC Plugin

There is an issue with the plugin or the odbc driver which wasn't built for the mac / arm architecture. 
Follow these instructions to build for x86 https://docs.docker.com/build/building/multi-platform/#support-on-docker-desktop

```
docker build \
  --build-arg "GRAFANA_VERSION=latest-ubuntu" \
  --build-arg "GF_INSTALL_PLUGINS=grafana-odbc-datasource" \
  -t grafana-custom .
```


## Start Docker Container

docker run -d -p 3000:3000 --name=grafana-custom grafana-custom

## Shell Access

docker exec -it -u 0 grafana-custom /bin/bash

## "odbcinst -j" Output

```
unixODBC 2.3.9
DRIVERS............: /etc/odbcinst.ini
SYSTEM DATA SOURCES: /etc/odbc.ini
FILE DATA SOURCES..: /etc/ODBCDataSources
USER DATA SOURCES..: /root/.odbc.ini
SQLULEN Size.......: 8
SQLLEN Size........: 8
SQLSETPOSIROW Size.: 8
```


