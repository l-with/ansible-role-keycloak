# Ansible Role Keycloak

Install Keycloak with docker-compose

## Collection dependencies

The role depends on the collection community.docker.
Note that this also requires installation of the python libraries `docker` and `docker-compose`.

## Role Variables

<!-- markdownlint-disable MD033 -->
| group | variable | default | description |
| --- | --- | ---| --- |
| docker | keycloak_db_image | `postgres:14.1-bullseye` | the postgres docker image |
| docker | keycloak_image | `bitnami/keycloak:16.1.1` | the keycloak docker image |
| docker | keycloak_container_name | `keycloak` | the container name for keycloak |
| docker | keycloak_postgres_container_name | `postgres` | the container name for postgres |
| docker | keycloak_postgres_container_data | `/var/lib/postgresql/data` | the path for the postgres_data volume |
| docker | keycloak_path | `/opt/keycloak` | the host keycloak_path (used for volume postgres_data) |
| docker | keycloak_docker_publish | <code>- "{{ keycloak_docker_publish_http }}"<br />- "{{ keycloak_docker_publish_https }}"</code> | the definition of docker publishing ports |
| docker | keycloak_docker_publish_http | `127.0.0.1:8080:8080` | definition of docker publishing http (use by `keycloak_docker_publish`) |
| docker | keycloak_docker_publish_https | `127.0.0.1:8443:8443` | definition of docker publishing https (use by `keycloak_docker_publish`) |
| docker | keycloak_docker_compose_state | `present` | state for [community.docker.docker_compose](https://docs.ansible.com/ansible/latest/collections/community/docker/docker_compose_module.html) |
| backup | keycloak_backup | `false` | if backup of the keycloak db should be configured and scheduled |
| backup | keycloak_configure_backup | `"{{ keycloak_backup }}"` | if backup of the keycloak db should be configured |
| backup | keycloak_backup_path | `/var/backups/keycloak` | the path for the keycloak backup |
| backup | keycloak_backup_file | `keycloak.dump` | the name of the keycloak backup file |
| backup | keycloak_backup_scripts_path | `/opt/keycloak/scripts` | the path for the backup scripts |
| backup | keycloak_backup_script_name | `"ansible_keycloak_backup.sh"` | the name of the keycloak backup script |
| backup | keycloak_restore_script_name | `"ansible_keycloak_restore.sh"` | the name of the keycloak restore script |
| backup | keycloak_backup_script |  `"{{ keycloak_backup_scripts_path }}/{{ keycloak_backup_script_name }}"` | the keycloak backup script |
| backup | keycloak_restore_script |  `"{{ keycloak_backup_scripts_path }}/{{ keycloak_restore_script_name }}"` | the keycloak restore script |
| backup | keycloak_schedule_backup | `"{{ keycloak_backup }}"` | if backup of the keycloak db should be scheduled |
| backup | keycloak_backup_cron_hour | `0` | the schedule hour for keycloak backup |
| backup | keycloak_backup_cron_minute | `0` | the schedule minute for keycloak backup |
| database | keycloak_db_name | `keycloak` | the database name |
| database | keycloak_db_user | `keycloak` | the database user |
| database | keycloak_db_password | | the password for the database user |
| user | keycloak_user | `kc-admin` | the keycloak user |
| user | keycloak_password | | the password for the keycloak user |
<!-- markdownlint-enable MD033 -->

## Dependencies

Requires docker-compose to be installed