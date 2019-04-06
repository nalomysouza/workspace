## workspace 
- Ambiente desenvolvimento

- Gerenciador de Docker (Portainer)

> $ docker volume create portainer_data
> $ docker run --name portainer --restart always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data -d portainer/portainer -p 9000:9000

- PostgreSQL 9.6 com postgis 2.5
> $ docker run --name pgsql96 --restart always -v pgsql_data:/var/lib/postgresql/data -e POSTGRES_PASSWORD=postgres -d mdillon/postgis:9.6 -p 5432:5432


- Sonar https://hub.docker.com/_/sonarqube
> $ docker run --name sonarqube -p 9001:9000 -e sonar.jdbc.username=postgres -e sonar.jdbc.password=postgres -e sonar.jdbc.url=jdbc:postgresql://127.0.0.1/sonar -v /dados/sonarqube:/opt/sonarqube -d sonarqube
