# postgres-docker
postgres-docker

## Build postresql docker container with image "postgres"

-d      = run in background
--name  = container name
-e      = set environment variable
-v      = mount volume/directory
image-name [:image-tag]
```bat
sudo docker container run   -d \
                            --name=postresql-container \
                            -p 5432:5432 \
                            -e POSTGRES_PASSWORD=Qwer1234 \
                            -e POSTGRES_USER=rickyfok \
                            -e POSTGRES_DB=crypto \
                            -e PGDATA=/pgdata \
                            -v /home/rickyfok/database/postgres:/pgdata \
                            --network nginx-net \
                            postgres:12.2-alpine

```

## Create docker container using image "docker-postresql"
```bat
sudo docker run --name postresql-container --network nginx-net -d docker-postresql
```


### Kill and Deploy command in sequency
```bat
sudo docker container stop postresql-container
sudo docker container rm postresql-container
sudo docker container run   -d \
                            --name=postresql-container \
                            -e POSTGRES_PASSWORD=Qwer1234 \
                            -e POSTGRES_USER=rickyfok \
                            -e POSTGRES_DB=crypto \
                            -e PGDATA=/pgdata \
                            -v /home/rickyfok/database/postgres:/pgdata \
                            --network nginx-net \
                            -p 5432:5432 \
                            postgres:12.2-alpine
```

### Execute command inside container
```bat
sudo docker exec -it postresql-container echo "I'm inside the container!"
sudo docker container exec -it postresql-container psql -U rickyfok
```
