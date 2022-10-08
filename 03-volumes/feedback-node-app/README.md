**Volumes**

```bash
docker run \
--rm \
--name feedback-node-app \
-p 3000:80 \
-v feedback-node-app:/app/feedback \
-v $(pwd):/app \
-d \
03-feedback-node-app:latest
```

**Read only volumes**

```bash
docker run \
--rm \
--name feedback-node-app \
-p 3000:80 \
-v feedback-node-app:/app/feedback \
-v $(pwd):/app:ro \
-d \
03-feedback-node-app:latest
```

**Environment variables and arguments**

> Set build arguments when building an image using `docker build` command.

```bash
docker build -t <image name>:<tag> --build-arg <argument name>=<value>

# Example
docker build -t feedback-node-app:latest --build-arg DEFAULT_PORT=8000
```

> Set environment variables when using `docker run` command.

```bash
docker run \
--rm \
--name feedback-node-app \
--env PORT=5000 \
-p 3000:5000 \
-v feedback-node-app:/app/feedback \
-v $(pwd):/app:ro \
-d \
03-feedback-node-app:latest
```

> Use environment variables file instead of setting them into `Dockerfile` to prevent exposing these values via `docker history <image>`.

```bash
docker run \
--rm \
--name feedback-node-app \
--env-file ./.env \
-p 3000:5000 \
-v feedback-node-app:/app/feedback \
-v $(pwd):/app:ro \
-d \
03-feedback-node-app:latest
```
