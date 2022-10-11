**Commands**

> Build

```bash
docker compose build \
--build-arg USER_ID=$(id -u) \
--build-arg GROUP_ID=$(id -g) \
```

> Run

```bash
docker compose run --rm npm <command>
```
