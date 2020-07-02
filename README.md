docker
======

List available mysql tags
```
wget -q https://registry.hub.docker.com/v1/repositories/mysql/tags -O - | jq '.[].name'
```

Remove all containers
```
sudo docker ps -a | grep 'ago' | awk '{print $1}' | xargs --no-run-if-empty sudo docker rm
```

Remove all images
```
sudo docker images --no-trunc | grep none | awk '{print $3}' | xargs sudo docker rmi
```

#### MySQL

```
docker run --name mydb -p3306:3306 -v /my/dev/data/lib/mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=abc123 -e MYSQL_DATABASE=myschema -e MYSQL_USER=myapp -e MYSQL_PASSWORD=abc123 -d mysql:5.7.30 --character-set-server=latin1

cat /my/dev/data/ddl.sql | docker exec -i mydb mysql -umyapp -pabc123 myschema
```


#### Postgres

https://registry.hub.docker.com/_/postgres/
```
docker run --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres
docker run -it --link some-postgres:postgres --rm postgres sh -c 'exec psql -h "$POSTGRES_PORT_5432_TCP_ADDR" -p "$POSTGRES_PORT_5432_TCP_PORT" -U postgres'
```
