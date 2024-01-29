# Instalación de Odoo

Lo que haremos en esta tarea será.

Configurar Odoo con docker-compose.
* Usar docker-compose
* Configura Postgresql y realizas pruebas
* Configura Odoo y enlazalo con el contenedor de Postgtresql
* Enlazar PyCharm con el docker y con la base de datos

## Docker-compose

Para poder comenzar tendremos que buscar la imagen de Odoo en [docker hub](http://hub.docker.com/_/odoo).

### Servicio de Odoo:

```docker
  web:
  image: odoo:16.0
  depends_on:
    - db
  ports:
    - "8069:8069"
  environment:
    - HOST=db
    - USER=odoo
    - PASSWORD=odoo
```

- Imagen: _odoo:16.0_

- Dependencias: El servicio de Odoo depende del servicio de base de datos (db).

- Puertos: Odoo estará en el puerto _8069_ del host.

- Variables de entorno:
  - **HOST**: Especifica el host de la base de datos.
  - **USER**: Especifica el usuario de la base de datos (en este caso, "odoo").
  - **PASSWORD**: Especifica la contraseña del usuario de la base de datos (en este caso, "odoo").

#### Servicio de PostgreSQL:

```docker
  db:
    image: postgres:15
    environment:
      - POSTGRES_DB=postgres
      - POSTGRES_PASSWORD=odoo
      - POSTGRES_USER=odoo
```

- Imagen: _postgres:15_

- Puertos:

    - PostgreSQL estará en el puerto _5433_ del host.

- Variables de Entorno:
    - **POSTGRES_DB**: Nombre de la base de datos (en este caso, "postgres").
    - **POSTGRES_USER**: Usuario de la base de datos (en este caso, "odoo").
    - **POSTGRES_PASSWORD**: Contraseña del usuario de la base de datos (en este caso, "odoo").

## Comandos docker

Para interactuar con este archivo `docker-compose.yml` tenemos una serie de comandos:
```
docker-compose up
```
Este comando se utiliza para crear e iniciar los servicios definidos en el archivo `docker-compose.yml`.

```
docker-compose up -d
```
Similar al comando anterior, pero se ejecuta en segundo plano.

```
docker-compose down
```
Detiene y elimina los contenedores, redes y volúmenes creados por el `docker-compose.yml``
```
docker-compose start
```
Inicia los contenedores existentes definidos en el archivo `docker-compose.yml`.

```
docker-compose stop
```
Detiene los contenedores definidos en el archivo `docker-compose.yml` **sin eliminarlos**.

```
docker-compose restart
```
Reinicia los contenedores.

```
docker-compose ps
```
Muestra el estado de los servicios.

### Testear conexión al servicio

Desde el desplegable derecho de 'Database' podemos hacer una nueva conexión de a Postgres.
