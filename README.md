# DataSaverApp

DataSaverApp es una aplicación desarrollada con Laravel que permite a los usuarios gestionar y guardar datos de manera eficiente. Este proyecto utiliza Docker para facilitar su despliegue y configuración.

## Instalación

Sigue estos pasos para clonar e instalar el proyecto:

### Clonar el proyecto

Clona el repositorio desde GitHub:

```bash
git clone https://github.com/lokogam/DataSaverApp.git
cd DataSaverApp   

## Requerimientos
Asegúrate de tener instalados los siguientes requisitos en tu máquina:

Docker
Docker Compose

## Configuración del entorno
Copia el archivo de configuración de ejemplo y actualiza las variables de entorno según sea necesario:

cp .env.example .env


Instalación de dependencias
Utiliza Docker para instalar las dependencias del proyecto con Composer:

docker run --rm \
    -u "$(id -u):$(id -g)" \
    -v "$(pwd):/var/www/html" \
    -w /var/www/html \
    laravelsail/php83-composer:latest \
    composer install --ignore-platform-reqs
    
    Levantar los servicios
Utiliza Docker Compose para levantar los servicios necesarios para el proyecto:
./vendor/bin/sail up


Migrar la base de datos
Ejecuta las migraciones para configurar la base de datos:
./vendor/bin/sail artisan migrate

Instalar y construir los assets de frontend
Instala las dependencias de npm y construye los assets:
./vendor/bin/sail artisan npm i
./vendor/bin/sail artisan npm run build



Acceder a la aplicación
La aplicación estará disponible en http://localhost.

Contribuciones
¡Las contribuciones son bienvenidas! Por favor, sigue el flujo de trabajo estándar de GitHub (fork, feature branch, pull request).

Licencia
Este proyecto está bajo la licencia MIT. Consulta el archivo LICENSE para más detalles.
