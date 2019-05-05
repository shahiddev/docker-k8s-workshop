## Docker commands cheat sheet

### Docker Images

**`docker image search`** searches for images on DockerHub
```
docker image search nginx
```

**`docker image pull`** downloads (pulls) images
```
docker image pull nginx
```

**`docker image ls`** lists pulled images
```
docker image ls
```

**`docker image rm`** removes images
```
docker image rm nginx
```

**`docker image build`** builds image
```
docker image build <Dockerfile>
```
```
-t, --tag : tag image
```

### Docker Containers

**`docker run`** creates and starts a container
```
docker run ubuntu 
```
```
--name : custom container name for easy reference

-i, --interactive : Allow you to input commands

-t, --tty : pseudo-terminal

-d, --detach : Run in background

-p, --publish 8080:80 : map port 80 in your container to 8080 on local host

-v, --volume : host/path:container/path

```



**`docker create`** creates a container without starting
```
docker create nginx 
```

**`docker ps`** lists containers
```
docker ps
```
```
-a, --all   : list all containers

-q, --quiet : only show IDs

-l, --latest : only show latest container
```

**`docker start`** starts (re-runs) a container
```
docker start <containerId>
```

**`docker stop`** stops a running container
```
docker stop <containerId>
docker ps -q | xargs docker stop
```

**`docker rm`** removes a container
```
docker rm <containerId>
docker ps -aq | xargs docker rm
```

**`docker exec`** execute a command in a *running* container
```
docker exec -it <containerId> echo hello-world
```
```
-i, --interactive : redirect STDIN

-t, --tty : pseudo-terminal
```

**`docker inspect`** inspects container
```
docker inspect <containerId>
```

**`docker history`** displays image layers
```
docker inspect <imagename>
```

### Docker Storage

**`docker volume ls`** list volumes
```
docker volume ls
```

**`docker volume inspect`** inspect volumes
```
docker volume inspect <containerId>
```

**`docker cp`** copy from container
```
docker cp <containerId>:/data/db /tmp/db
docker cp /tmp/db <containerId>:/data/db
```

More details: https://docs.docker.com/engine/reference/commandline/docker/