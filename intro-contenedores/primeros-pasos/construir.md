Para crear un contenedor necesitamos un Dockerfile.

Para empezar, creemos una carpeta y entremos a ella:

`mkdir ejercicio && cd ejercicio`{{exec}}

Primero, creemos un archivo `hello.py` y pega lo siguiente:
```
from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello_world():
    return "<p>Hello, World!</p>"
```

Luego un `requirements.txt` para las dependencias:

`echo Flask > requirements.txt`{{exec}}

Ahora el archivo `Dockerfile`:

```
FROM python:3.13-slim
WORKDIR /usr/local/app

# Install the application dependencies
COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

# Copy in the source code
COPY hello.py ./
EXPOSE 5000

# Setup an app user so the container doesn't run as the root user
RUN useradd app
USER app

CMD ["flask", "--app", "hello", "--host", "0.0.0.0", "run"]
```

Crear la imagen:

`docker build -t python-app .`{{exec}}

Verificar que está en nuestro sistema:

`docker image ls`{{exec}}

Correr nuestro contenedor:

`docker run -d -p 5000:5000 --name my-python-app-container python-app`{{exec}}

Verificar que funciona:
`curl localhost:5000`

Revisar los logs:
`docker container logs my-python-app-container`{{exec}}

Ahora, si queremos subirlo a un repositorio, tenemos que cambiar el tag primero:

```
random_tag=$(openssl rand -hex 12)
docker tag python-app ttl.sh/python-app-${random_tag}
```{{exec}}

Ahora lo podemos subir:
`docker push ttl.sh/python-app-${random_tag}`{{exec}}

**NOTA:** `ttl.sh` es un repositorio público y gratis que borrar las imágenes
subidas después de 24 horas. En casos de uso verdaderos, debemos usar un repositorio
que nos permita subir imágenes usando autenticación y que podamos tener imágenes
privadas.