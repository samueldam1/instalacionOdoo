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

- Imagen: _odoo:16.0_

- Dependencias: El servicio de Odoo depende del servicio de base de datos (db).

- Puertos: Odoo estará en el puerto _8069_ del host.

- Variables de entorno:
  - **HOST**: Especifica el host de la base de datos.
  - **USER**: Especifica el usuario de la base de datos (en este caso, "odoo").
  - **PASSWORD**: Especifica la contraseña del usuario de la base de datos (en este caso, "odoo").

#### Servicio de PostgreSQL:

- Imagen: _postgres:15_

- Puertos:

    - PostgreSQL estará en el puerto _5433_ del host.

- Variables de Entorno:

    - POSTGRES_DB: Nombre de la base de datos (en este caso, "postgres").
    - POSTGRES_USER: Usuario de la base de datos (en este caso, "odoo").
    - POSTGRES_PASSWORD: Contraseña del usuario de la base de datos (en este caso, "odoo").

### Testear conexión al servicio

Desde el desplegable derecho de 'Database' podemos hacer una nueva conexión de a Postgres.
