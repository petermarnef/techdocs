#Run a local SQL server in docker

Linux image: https://hub.docker.com/_/microsoft-mssql-server

Create a new docker container:
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=<pwd>' -p 1433:1433 -v C:\MyStuff\Docker\MSSQL:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest

Run existing container:
docker start <container_id>