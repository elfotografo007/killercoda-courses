Ejecuta el siguiente comando en una terminal:

`docker run -it ubuntu:25.04`{{exec}}

El comando funciona así:
- `docker` es el ejecutable de Docker
- `run` le indica a Docker que quiero correr un contenedor
- `-it` son dos banderas: `--interactive` y `--tty` que nos permite conectarnos
a la salida estándar del contenedor y ejecutar comandos.
- `ubuntu:25.04` es la imagen a partir de la cual quiero crear el contenedor. `ubuntu` es el nombre de la imagen y `25.04` es el tag. Si omito el tag, se usará la imagen más reciente

Ahora corre un comando:

`cat /etc/os-release`{{exec}}

Para salir de la terminal del contenedor:

`exit`{{exec}}