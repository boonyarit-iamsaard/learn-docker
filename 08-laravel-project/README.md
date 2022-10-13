**Create a laravel project**

```bash
docker compose run --rm composer create-project --prefer-dist laravel/laravel .
```

**Update the laravel project `.env` file**

```env
...
DB_CONNECTION=mysql
DB_HOST=mysql # This is the name of the service in docker-compose.yml
DB_PORT=3306
DB_DATABASE=<YOUR_DATABASE_NAME>
DB_USERNAME=<YOUR_USERNAME>
DB_PASSWORD=<YOUR_PASSWORD>
...
```

**Run a project**

```bash
docker compose up --build -d server
```

**Using `yarn` command**

```bash
docker compose run --rm yarn <command>
```

**Using `composer` command**

```bash
docker compose run --rm composer <command>
```

**Using `artisan` command**

```bash
docker compose run --rm artisan <command>
```
