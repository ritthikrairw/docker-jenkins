### Backup container volume

Backup volume

`docker run --rm --volumes-from <CONTAINER ID OR NAME> -v $(pwd):/backup busybox sh -c "tar -zcvf /backup/backup.tar.gz -C /var/jenkins_home ."`


### Restore container volume

Remove container

`docker rm -f <CONTAINER ID OR NAME>`

Remove volume

`docker volume rm <VOLUME ID OR NAME>`

Create a new volume

`docker volume create <VOLUME ID OR NAME>`

Copy backup data to a new volume

`docker run --rm -v <VOLUME ID OR NAME>:/var/jenkins_home -v $(pwd):/backup busybox sh -c "cd /var/jenkins_home && tar -zxvf /backup/backup.tar.gz"`

Re-create container

`docker compose up -d`