Ahora vamos a ver los comandos básicos de Docker.

Empecemos por el comando para ver los contenedores corriendo actualmente:

`docker ps`{{exec}}

Debemos ver que el contenedor de redis todavía está corriendo. Detengamos dicho contenedor

`docker stop CONTENEDOR`

Ahora, miremos la lista de contenedores que existen en nuestro sistema:

`docker container ls -a`{{exec}}

Esta lista muestra incluso contendores detenidos. Si queremos borrar algún contenedor:

`docker rm CONTENEDOR`

Para ver las imágenes descargadas en nuestro computador:

`docker image ls`{{exec}}

Para descargar una imagen sin ejecutarla:

`docker pull mysql`{{exec}}

Para borrar una imagen que no necesitemos más:

`docker image rm mysql`{{exec}}