# MongoDB

## Getting Started

**Prerequisites:** [Docker](https://www.docker.com/get-started) must be installed.

To get started, you can run the following command:

```bash
docker compose up -d
```

This will start a [MongoDB](https://hub.docker.com/_/mongo) and [mongo-express](https://hub.docker.com/_/mongo-express) container. You can access the mongo-express web interface at [http://localhost:8081].

### Container access and viewing logs

You can access the container with the following command:

```bash
docker exec -it mongo-db bash
```

You can view the logs of the container with the following command:

```bash
docker logs mongo-db -f --tail 100
```

**Note:** Replace `mongo-db` with the name of the container you want to access or view logs for.

### Connecting to the MongoDB container

```bash
docker run -it --rm --network mongo-net mongo \
	mongosh --host mongo \
		-u admin \
		-p pass \
		--authenticationDatabase admin \
		admin
```

**Note:**

- `--network mongo-net` is used to connect to the `mongo-net` network.
- `--host mongo` is used to connect to the mongo container. `mongo` is the name of the service in the `compose.yml` file. Learn more about [Docker Compose networking](https://docs.docker.com/compose/networking/).
- `-u admin` is the username.
- `-p pass` is the password.
- `--authenticationDatabase admin` is the authentication database.
- `admin` is the database to connect to.

### (optional) Using MongoDB Compass or Shell

You can also install [MongoDB Compass](https://www.mongodb.com/try/download/compass) (GUI) or [MongoDB Shell](https://www.mongodb.com/try/download/shell) to connect to the MongoDB container. You can use the following connection string:

```
mongodb://admin:pass@localhost:27017/
```

### Stopping the containers

To stop the containers, you can run the following command:

```bash
docker compose down
```
