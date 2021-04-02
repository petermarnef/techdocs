# How to
## Run a local SQL server in docker

Linux image: https://hub.docker.com/_/microsoft-mssql-server

**Create a new docker container**

```docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=<pwd>' -p 1433:1433 -v C:\MyStuff\Docker\MSSQL:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest```

**Run existing container**

```docker start <container_id>```

## Basics

Create image based on local Dockerfile

``` bash
docker build .
```

Force build with no-cache

``` bash
docker build --no-cache .
```

Create images based on local Dockerfile and give the image a name (a tag)

``` bash
docker build . -t <tagname>
```

Run docker image

``` bash
docker run <image tag>
```

Run docker images and immediately remove container (don't pollute your system)

``` bash
docker run --rm <image tag>
```

List running containers

``` bash
docker ps
```

List containers that are stopped

``` bash
docker ps -a
```

List images

``` bash
docker images
```

Run a container interactively and remove it afterwards

``` bash
docker run -it --rm <image tag>
```

Connect interactively to a running container

``` bash
docker exec -ti <container> bash
```

Run a container in the background

``` bash
docker run -d --rm <image>
```
