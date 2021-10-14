# Ansible Role Keycloak

Install Keycloak with docker-compose

## Collection dependencies

The role depends on the collection community.docker.
Note that this also requires installation of the python libraries `docker` and `docker-compose`.

## Role Variables

### Docker Compose
#### `keycloak_db_image`: `postgres:13.3-alpine`

the postgres docker image

#### `keycloak_image`: `jboss/keycloak:15.0.1`

the keycloak docker image

#### `keycloak_container_name`: `keycloak`

the container name for keycloak

#### `keycloak_postgres_container_name`: `postgres`

the container name for postgres

#### `keycloak_docker_publish`:

```yaml
  - "{{ keycloak_docker_publish_http }}"
  - "{{ keycloak_docker_publish_https }}"
```

the definition of docker publishing ports

#### `keycloak_docker_publish_http`: `127.0.0.1:8080:8080`

definition of docker publishing http (use by `keycloak_docker_publish`)

#### `keycloak_docker_publish_https`: `127.0.0.1:8443:8443`

definition of docker publishing https (use by `keycloak_docker_publish`)

#### `keycloak_docker_compose_state`: `present`

state for [community.docker.docker_compose](https://docs.ansible.com/ansible/latest/collections/community/docker/docker_compose_module.html)

### Backup
#### `keycloak_backup`: `no`

if backup of the keycloak db should be configured

The backup script is templated to `/root/ansible_keycloak_backup.sh`.

#### `keycloak_backup_path`: `/var/backups/keycloak`

the path for the keycloak backup

#### `keycloak_backup_file`: `keycloak.dump`

the name of the keycloak backup file

#### `keycloak_backup_script`: `/root/ansible_keycloak_backup.sh`

the path for the keycloak backup script

#### `keycloak_restore_script`: `/root/ansible_keycloak_restore.sh`

the path for the keycloak restore script

#### `keycloak_backup_cron_hour`: `0`

the schedule hour for keycloak backup

#### `keycloak_backup_cron_minute`: `0`

the schedule minute for keycloak backup

### Database
#### `keycloak_db_name`: `keycloak`

the database name

#### `keycloak_db_user`: `keycloak`

the database user

#### `keycloak_db_password`

the password for the database user

### Keycloak admin

#### `keycloak_user`: `kc-admin`

the keycloak user

#### `keycloak_password`

the password for the keycloak user

## Dependencies

Requires docker-compose to be installed