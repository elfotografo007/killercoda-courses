Ahora agreguemos el archivo de Docker compose:

`touch compose.yaml`{{exec}}

Copia y pega lo siguiente:

```
services:
  app:
    image: node:18-alpine
    command: sh -c "yarn install && yarn run dev"
    ports:
      - 127.0.0.1:3000:3000
    working_dir: /app
    volumes:
      - ./:/app
    environment:
      MYSQL_HOST: mysql
      MYSQL_USER: root
      MYSQL_PASSWORD: secret
      MYSQL_DB: todos

  mysql:
    image: mysql:8.0
    volumes:
      - todo-mysql-data:/var/lib/mysql
    environment:
      MYSQL_ROOT_PASSWORD: secret
      MYSQL_DATABASE: todos

volumes:
  todo-mysql-data:
```{{copy}}

Arranquemos todos los servicios:

`docker compose up -d`{{exec}}

Revisemos los logs:

`docker compose logs`{{exec}}

Ahora puedes ver la aplicación corriendo en {{TRAFFIC_HOST1_3000}}

Detener la aplicación

`docker compose stop`{{exec}}

Matar la aplicación *borrando todo*:
`docker compose down`{{exec}}
