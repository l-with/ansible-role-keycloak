# Ansible Role Keycloak
Install Keycloak with docker-compose

## Collection dependencies
The role depends on the collection community.docker.
Note that this also requires installation of the python libraries `docker` and `docker-compose`.
## Role Variables

#### `keycloak_db_image`: `postgres:13.3-alpine`
the postgres docker image

#### `keycloak_image`: `jboss/keycloak:13.0.1`
the keycloak docker image

#### `keycloak_db_name`: `keycloak`
the database name
#### `keycloak_db_user`: `keycloak`
the database user 

#### `keycloak_db_password`
the password for the database user

#### `keycloak_user`: `kc-admin`
the keycloak user

#### `keycloak_password`
the password for the keycloak user

#### `keycloak_docker_compose_state`: `present`
state for [community.docker.docker_compose](https://docs.ansible.com/ansible/latest/collections/community/docker/docker_compose_module.html)