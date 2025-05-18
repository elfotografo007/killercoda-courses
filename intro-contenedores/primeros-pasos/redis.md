No todos los contenedores tienen que ser interactivos. La mayoría de
contenedores simplemente corren en segundo plano de manera indefinida.

Por ejemplo, el siguiente comando corre un contenedor de redis:

`docker run -d -p 6390:6379 redis`{{exec}}

El comando funciona así:
- `docker` es el ejecutable de Docker
- `run` le indica a Docker que quiero correr un contenedor
- `-d` le indica a Docker que lo corra en segundo plano
- `-p` es para exponer o mapear puertos. Funciona `[HOST]:[CONTENEDOR]`, de manera que el puerto **6379** del contenedor es expuesto en el puerto **6390** del host.

Verifiquemos que el contenedor está corriendo:

`docker ps`{{exec}}

Ahora instalemos y arranquemos la línea de comandos de redis para jugar:

```
apt update && apt install -y redis-tools
redis-cli -p 6390
```{{exec}}

Algunos comandos de ejemplo:

```
set hola 'mundo'
set hello 'world'
get hola
keys *
```{{exec}}

Salir de redis:
`exit`{{exec}}

Como pueden ver, pudimos instalar e interactuar con un servidor
de base de datos de manera sencilla y fácil. Con esto podemos incluso
correr varios contenedores de redis al mismo tiempo, utilizando
versiones disintas si es necesario. De la misma manera puedo correr otros servidores como `mysql` o `postgres`.

**ADVERTENCIA:** Los contenedores tienen una naturaleza efímera y si
no se tiene cuidado, se puede perder la información dentro de las bases de datos.