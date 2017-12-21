# BELK stack example with Docker

BELK stack in docker to read logs from log directory with Filebeat, parse in Logstash, store in Elasticsearch and display in Kibana. Logs are from 12/Dec/2017 to 18/Dec/2017 (take a look on that to search in Kibana).

The containers are shipped with X-Pack installed.

In some cases, it is need to set up the vm.max_map_count=262144 for Elasticsearch.

The example data are from the month of September 2017. The logs will be read from the ./logs/ directory.

If you need Filebeta dashboards in Kibana switch to [filebeat_dashboards branch](https://github.com/aalmazanarbs/simple-docker-belk/tree/filebeat_dashboards)

Tested on docker 17.09.1-ce.

## Build and start environment

```shell
docker-compose up -d
```

or stop and start environment
```shell
docker stop elasticsearch6.1.0 logstash6.1.0 kibana6.1.0 filebeat6.1.0
docker-compose up -d
```

or delete and restart environment

```shell
docker stop elasticsearch6.1.0 logstash6.1.0 kibana6.1.0 filebeat6.1.0
docker rm elasticsearch6.1.0 logstash6.1.0 kibana6.1.0 filebeat6.1.0
docker-compose up -d
```

## Stop environment

```shell
docker stop elasticsearch6.1.0 logstash6.1.0 kibana6.1.0 filebeat6.1.0
```

## Reset a service

Instead of restart the application, just restart the container:
```shell
docker restart container_name
```

## Kibana access

[http://localhost:5601/](http://localhost:5601/)
```
username: elastic
password: changeme
```

## Elasticsearch API access

```shell
curl -u elastic:changeme http://localhost:9200/
```

## Logs

All logs
```shell
docker-compose logs -f
```

Single container
```shell
docker logs -f container_name
```

## Get bash in a container
```shell
docker exec -it container_name bash
```

## Directory layout

- Config for Elasticsearch, Logstash, Filebeat and Kibana: ../config/
- Logs to be read by Filebeat: ../logs/
- docker-compose.yml: the definition of BELK architecture

## Disable X-Pack

```yml
xpack.watcher.enabled: false # in elasticsearch.yml
xpack.security.enabled: false
xpack.monitoring.enabled: false
xpack.watcher.enabled: false
xpack.graph.enabled: false
```
