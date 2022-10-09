**Create network**

```bash
docker network create multi-containers
```

**Create and run mongodb container**

```bash
docker run \
--name mongodb \
--network multi-containers \
-p 27017:27017 \
-v multi-containers-data:/data/db \
-e MONGO_INITDB_ROOT_USERNAME=<username> \
-e MONGO_INITDB_ROOT_PASSWORD=<password> \
-d \
mongo

# Publish to localhost on port 27017 for ability to access from outside the container.
# Create named volume to persist data.
# Create a user with root permissions with specified username and password.

# Connection string for connecting from another container
# mongodb://<user>:<password>@mongodb:27017/multi-containers?authSource=admin

# Connection string for connecting from outside the container
# mongodb://<user>:<password>@localhost:27017/multi-containers?authSource=admin
```

**Create and run backend container**

```bash
# Build docker image for backend
docker build -t multi-containers-backend:latest .

# Run backend container based on multi-containers-backend:latest
# Beaware of binding working directory path inside the container to the source folder
docker run \
--name multi-containers-backend \
--network multi-containers \
-v $(pwd):/app \
-v logs:/app/logs \
-v /app/node_modules \
-p 80:80 \
-d \
multi-containers-backend:latest
```

**Create and run frontend container**

```bash
# Build docker image for backend
docker build -t multi-containers-frontend:latest .

# Run backend container based on multi-containers-backend:latest
# Beaware of binding working directory path inside the container to the source folder
docker run \
--name multi-containers-frontend \
--network multi-containers \
-p 3000:3000 \
-v $(pwd):/app \
-v /app/node_modules \
-it \
-d \
multi-containers-frontend:latest
```
