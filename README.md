## workspace 
- Ambiente desenvolvimento

- Gerenciador de Docker (Portainer)

> $ docker volume create portainer_data
> $ docker run --name portainer --restart always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data -d portainer/portainer -p 9000:9000

- PostgreSQL 9.6 com postgis 2.5
> $ docker run --name pgsql96 --restart always -v pgsql_data:/var/lib/postgresql/data -e POSTGRES_PASSWORD=mysecretpassword -d mdillon/postgis:9.6 -p 5432:5432
