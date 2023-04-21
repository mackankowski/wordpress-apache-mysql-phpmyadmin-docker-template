# Wordpress - Docker container template

- [Prerequisites](#prerequisites)
- [Setup](#setup)
- [Migration](#migration)
- [Troubleshooting](#troubleshooting)

## Prerequisites

Required software:

- Docker: https://docs.docker.com/get-docker/

## Setup

0: Run Docker, e.g. by using Colima: [Install & run Docker on macOS (gist)](https://gist.github.com/mackankowski/7b6b1d861359d31b8a28195432d86d4d)

1. Pull the repository

2. In the root directory, run: `docker compose up` (or `docker-compose up`)

The website will available at http://localhost (:80)

(Also, there is phpadmin available at http://localhost:8081)

3. To stop application container, run: `docker compose down`

For more commands, go to: https://docs.docker.com/engine/reference/commandline/docker/

## Migration

1. For both, local and remote instance of Wordpress, install the plugin: https://wordpress.org/plugins/all-in-one-wp-migration/

2. For the local instance, open Wordpress admin dashboard and find `All-In-One-WP-Migration/Export` tab

3. Fill the field: "Find **text** Replace with **another-text** in the database, e.g. "Find **localhost** Replace with **yoursite.com** in the database or **http://** to **https://**" (replacing `http://localhost` to `https://yoursite.com` should be enough)

4. Choose "Export to file" and wait for finishing - the backup file will be saved on your local machine

5. For the remote website instance, open Wordpress admin dashboard and find `All-In-One-WP-Migration/Import` tab

6. Click "Import from file", find save backup file, confirm and wait for completion

## Troubleshooting

### Bind for 0.0.0.0:8081 failed: port is already allocated

Run the following command to identify the container which uses the port and remove it:

```
docker container ls
docker rm -f <container-name>
```

or remove all containers at once:

`
docker stop $(docker ps -a -q)
docker rm $(docker ps -a -q)
`
