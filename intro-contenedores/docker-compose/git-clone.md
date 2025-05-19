Clona la aplicación:

`git clone https://github.com/docker/getting-started-app.git`{{exec}}

`cd getting-started-app`{{exec}}

Ahora agreguemos el `Dockerfile`

`touch Dockerfile`{{exec}}

Abre el archivo en el IDE y pega lo siguiente:

```
FROM node:lts-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "src/index.js"]
EXPOSE 3000
```

Construye el contendor:
`docker build -t getting-started .`{{exec}}