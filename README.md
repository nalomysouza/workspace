## workspace 
- Ambiente desenvolvimento

- Gerenciador de Docker (Portainer)

> $ docker volume create portainer_data
> $ docker run --name portainer --restart always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data -d portainer/portainer -p 9000:9000

- PostgreSQL 9.6 com postgis 2.5
> $ docker run --name pgsql96 --restart always -v pgsql_data:/var/lib/postgresql/data -e POSTGRES_PASSWORD=postgres -d mdillon/postgis:9.6 -p 5432:5432

- GitLab https://docs.gitlab.com/omnibus/docker/
> sudo docker run --detach \
  --hostname gitlab.example.com \
  --publish 443:443 --publish 80:80 --publish 22:22 \
  --name gitlab \
  --restart always \
  --volume /srv/gitlab/config:/etc/gitlab \
  --volume /srv/gitlab/logs:/var/log/gitlab \
  --volume /srv/gitlab/data:/var/opt/gitlab \
  gitlab/gitlab-ce:latest
  
  Backup STRATEGY=copy para evitar file changed as we read it https://docs.gitlab.com/omnibus/settings/backups.html
  > docker exec -t <container> gitlab-rake gitlab:backup:create
  Realizar Backup das Configurações 
  > docker exec -t <container> /bin/sh -c 'umask 0077; tar cfz /secret/gitlab/backups/$(date "+etc-gitlab-\%s.tgz") -C / etc/gitlab'
  You need to have volumes mounted at /secret/gitlab/backups and /var/opt/gitlab in order to have these backups persisted outside the container.

- Sonar https://hub.docker.com/_/sonarqube
> $ docker run --name sonarqube -p 9001:9000 -e sonar.jdbc.username=postgres -e sonar.jdbc.password=postgres -e sonar.jdbc.url=jdbc:postgresql://127.0.0.1/sonar -v /dados/sonarqube:/opt/sonarqube -d sonarqube

- PGadmin4 (https://hub.docker.com/r/dpage/pgadmin4/)
> $ docker run -p 9004:80 -e "PGADMIN_DEFAULT_EMAIL=user@domain.com" -e "PGADMIN_DEFAULT_PASSWORD=SuperSecret" -d dpage/pgadmin4
