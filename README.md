# docker-glances

## Description:

This docker image provide a [glances](https://glances.readthedocs.io/en/stable/index.html) service based on [Alpine Linux](https://hub.docker.com/_/alpine/)

## Usage:
### Run glances in console mode
```
docker run --name glances -it -p 61208-61209:61208-61209 \
-v /var/run/docker.sock:/var/run/docker.sock:ro \
--pid host \
--restart=always aknaebel/glances
```

### Run glances using custom config file
```
docker run --name glances -it -p 61208-61209:61208-61209 \
-v /glances/glances.conf:/glances/conf/glances.conf \
-v /var/run/docker.sock:/var/run/docker.sock:ro \
--pid host \
--restart=always aknaebel/glances
```

## Docker-compose:
``` 
version: '2'
services:
    glances:
        image: aknaebel/glances
        ports:
            - "61208-61209:61208-61209"
        volumes:
            - /var/run/docker.sock:/var/run/docker.sock:ro
        restart: always
        pid: "host"
```

```
docker-compose up -d
```
