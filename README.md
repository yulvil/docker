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
