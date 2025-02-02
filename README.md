# Wordpress - Docker container template

- [Prerequisites](#prerequisites)
- [Setup](#setup)
- [Migration](#migration)
- [Troubleshooting](#troubleshooting)

## Prerequisites (macOS)

Required software:

- [Homebrew](https://brew.sh/)

- `brew install colima`
- `brew install kubectl`
- `brew install docker`
- `brew install docker-compose`

## Running

0. [Install & run Docker on macOS (gist)](https://gist.github.com/mackankowski/7b6b1d861359d31b8a28195432d86d4d) 

1. Set environment: `chmod +x env.sh && source env.sh`

2. Run the app: `docker-compose up`

The Wordpress app will be available at http://localhost:8080

The phpMyAdmin dashboard will be available at http://localhost:9090

3. To stop the application container, run: `docker-compose down`

For more commands, go to: https://docs.docker.com/engine/reference/commandline/docker/

## Migration

1. For both, local and remote instances of WordPress, install the plugin: https://wordpress.org/plugins/all-in-one-wp-migration/

2. For the local instance, open WordPress admin dashboard and find `All-In-One-WP-Migration/Export` tab

3. Fill the field: "Find **text** Replace with **another-text** in the database, e.g. "Find **localhost** Replace with **yoursite.com** in the database or **http://** to **https://**" (replacing `http://localhost` to `https://yoursite.com` should be enough)

4. Choose "Export to file" and wait for finishing - the backup file will be saved on your local machine

5. For the remote website instance, open WordPress admin dashboard and find `All-In-One-WP-Migration/Import` tab

6. Click "Import from file", find save the backup file, confirm, and wait for completion

## Docker commands

Remove all containers:

`docker rm $(docker ps -aq) -f`

Remove all images:

`docker rmi $(docker images -aq) -f`

Both actions at once:

`docker rm $(docker ps -aq) -f && docker rmi $(docker images -aq) -f`