# influxDB

Initial setup:
```
$ docker run --rm \
      -e INFLUXDB_DB=monitoring \
      -e INFLUXDB_ADMIN_USER=admin -e INFLUXDB_ADMIN_PASSWORD=IamIronMan \
      -e INFLUXDB_USER=telegraf -e INFLUXDB_USER_PASSWORD=stalkerPaparazzi \
      -v $PWD/influxdb:/var/lib/influxdb \
      influxdb /init-influxdb.sh
```

Run after initial set up:
```
$ docker run -d -p 8086:8086 -v $PWD/influxdb:/var/lib/influxdb --name influxDB influxdb
```

# Grafana
admin IamIronMan
```
$ docker run -d -p 3000:3000 -v $PWD/grafana:/var/lib/grafana --name grafana grafana/grafana
```

docker run  -d --net=container:influxDB --name telegraf-influxDB telegraf

docker run -d --name=telegraf --net=monitoring -v $PWD/Developer/ZOE/telegraf.conf:/etc/telegraf/telegraf.conf:ro telegraf





docker run -d \
    --name Chainlink-Postgres \
    -e POSTGRES_PASSWORD=mysecretpassword \
    -e PGDATA=/var/lib/postgresql/data/pgdata \
    -v /custom/mount:/var/lib/postgresql/data \
    postgres