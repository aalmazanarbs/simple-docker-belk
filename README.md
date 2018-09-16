# BELK stack example with Docker

BELK stack in docker to read logs from log directory with Filebeat, parse in Logstash, store in Elasticsearch and display in Kibana. Logs are from 10/Sep/2018 to 16/Sep/2018 (take a look on that to search in Kibana).

In some cases, it is need to set up the vm.max_map_count=262144 for Elasticsearch.

The example data are from the month of September 2018. The logs will be read from the ./logs/ directory.

Tested on docker 18.06.1-ce.

## Build and start environment

```shell
docker-compose up -d
```

or stop and start environment
```shell
docker-compose stop
docker-compose up -d
```

or delete and restart environment

```shell
docker-compose rm -fs
docker-compose up -d
```

## Stop environment

```shell
docker-compose stop
```

## Reset a service

Instead of restart the application, just restart the container:
```shell
docker restart container_name
```

## Kibana access

[http://localhost:5601/](http://localhost:5601/)

## Elasticsearch API access

```shell
curl http://localhost:9200/
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
