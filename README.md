# Docker Compose 01: first service

A SKILL.SCH lab: run a web server from a single `compose.yml` instead of a long `docker run` command.

## The file

```yaml
services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
```

- `services.web` is the container's name inside the project.
- `image: nginx:latest` pulls the official nginx image.
- `"8080:80"` maps port 8080 on your machine to port 80 in the container.

## Run it

```bash
docker compose up -d
docker compose ps
curl -I http://localhost:8080   # HTTP/1.1 200 OK, Server: nginx
```

Open http://localhost:8080 to see the nginx welcome page.

## Inspect and stop

```bash
docker compose logs web
docker compose down
```

## Next steps

- Mount your own page: add `volumes: ["./site:/usr/share/nginx/html:ro"]`.
- Add a second service (for example Redis) and connect them on the default network.
