# docker basic commands

### creating a docker container in one line
docker run --name <containername> -d -p 8080:80 <containername>
```
// -d => run detached mode
// -p => port
// --name => containername
```

### removing all containers
docker rm $(docker ps -aq) -f

### removing one container forcing
docker rm <ID_NAME> -f

### list all containers (even those stopped)
docker ps -a

## copying localFile inside the container
docker cp /path/to/local/file container_name:/tmp/

## executing a container
docker exec -it <container_name> bash

## creating a pgsql image in one line:
```
docker run -d \
    --name pgsql-db \
    -e POSTGRES_DB=database \
    -e POSTGRES_USER=user \
    -e POSTGRES_PASSWORD=psswd \
    -p 5432:5432 \
    -v .:/var/lib/postgresql/data \
    --network mynetwork
    postgres:latest
```

## removing images with ``<none>``
``docker rmi $(docker images -a -q -f "dangling=true")``

## removing containers with status "Exited"
``docker rm $(docker ps -a -f status=exited -q)``
