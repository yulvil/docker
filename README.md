docker
======

Remove all containers
```
sudo docker ps -a | grep 'ago' | awk '{print $1}' | xargs --no-run-if-empty sudo docker rm
```

Remove all images
```
sudo docker images --no-trunc | grep none | awk '{print $3}' | xargs sudo docker rmi
```

#### Postgres

https://registry.hub.docker.com/_/postgres/
```
docker run --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres
docker run -it --link some-postgres:postgres --rm postgres sh -c 'exec psql -h "$POSTGRES_PORT_5432_TCP_ADDR" -p "$POSTGRES_PORT_5432_TCP_PORT" -U postgres'
```
