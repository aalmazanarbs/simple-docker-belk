# BELK stack example with Docker

The containers are shipped with X-Pack installed.

In some cases, it is need to set up the vm.max_map_count=262144 for Elasticsearch.

The example data are from the month of September 2017. The logs will be read from the ./logs/ directory.

Tested on docker 17.09.0-ce.

## Build and start environment

```shell
docker-compose up -d
```

or stop and start environment
```shell
docker stop elasticsearch5.6 logstash5.6 kibana5.6 filebeat5.6
docker-compose up -d
```

or delete and restart environment

```shell
docker stop elasticsearch5.6 logstash5.6 kibana5.6 filebeat5.6
docker rm elasticsearch5.6 logstash5.6 kibana5.6 filebeat5.6
docker-compose up -d
```

## Stop environment

```shell
docker stop elasticsearch5.6 logstash5.6 kibana5.6 filebeat5.6
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
- docker-compose.yml: the definition of ELK architecture

## Disable X-Pack

```yml
xpack.watcher.enabled: false # in elasticsearch.yml
xpack.security.enabled: false
xpack.monitoring.enabled: false
xpack.watcher.enabled: false
xpack.graph.enabled: false
```
