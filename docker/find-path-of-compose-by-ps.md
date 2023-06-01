# How to find location of compose.yaml by running docker container

list all running containers
```
docker ps
```
copy one  CONTAINER_ID of containers that you want to stop
```
docker inspect <container_id> | grep 'compose.project.working_dir'
```
navigate to the path, check compose.yaml and shutdown the compose stack

```
docker compose down
```

