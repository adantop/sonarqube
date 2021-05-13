# sonarqube

SonarQube installation with PostgreSQL. Used all defaults and they can be updated by changing the environment file present in `config/local.env`

## How to run

1. Set ulimits since sonarqube uses elasticsearch (once)

    ```shell
        sudo su
        sysctl -w vm.max_map_count=262144
        sysctl -w fs.file-max=65536
        ulimit -n 65536
        ulimit -u 4096
    ```

1. Create volumes (once)

    ```shell
        docker volume create sonarqube-pg-data
        docker volume create sonarqube-pgadmin-data
        docker volume create sonarqube-data
        docker volume create sonarqube-extensions
        docker volume create sonarqube-logs
    ```

1. Run with Docker Compose

    ```shell
        cd <project root>
        docker-compose --env-file ./config/local.env up -d
    ```

1. Delete the deployment

    ```shell
        cd <project root>
        docker-compose down
    ```
