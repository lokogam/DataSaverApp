
# DataSaverApp

DataSaverApp es una aplicaciÃ³n desarrollada con Laravel que permite a los usuarios gestionar y guardar datos de manera eficiente. Este proyecto utiliza Docker para facilitar su despliegue y configuraciÃ³n.

## InstalaciÃ³n

Sigue estos pasos para clonar e instalar el proyecto:

### Clonar el proyecto

Clona el repositorio desde GitHub:

```bash
git clone https://github.com/lokogam/DataSaverApp.git
cd DataSaverApp
```

## Requerimientos

AsegÃºrate de tener instalados los siguientes requisitos en tu mÃ¡quina:

- Docker
- Docker Compose

## ConfiguraciÃ³n del entorno

Copia el archivo de configuraciÃ³n de ejemplo y actualiza las variables de entorno segÃºn sea necesario:

```bash
cp .env.example .env
```

## InstalaciÃ³n de dependencias

Utiliza Docker para instalar las dependencias del proyecto con Composer:

```bash
docker run --rm     -u "$(id -u):$(id -g)"     -v "$(pwd):/var/www/html"     -w /var/www/html     laravelsail/php83-composer:latest     composer install --ignore-platform-reqs
```

## Levantar los servicios

Utiliza Docker Compose para levantar los servicios necesarios para el proyecto:

```bash
./vendor/bin/sail up
```

## Migrar la base de datos

Ejecuta las migraciones para configurar la base de datos:

```bash
./vendor/bin/sail artisan migrate
```

## Instalar y construir los assets de frontend

Instala las dependencias de npm y construye los assets:

```bash
./vendor/bin/sail npm install
./vendor/bin/sail npm run build
```

## Acceder a la aplicaciÃ³n

La aplicaciÃ³n estarÃ¡ disponible en [http://localhost](http://localhost).

## Contribuciones

Â¡Las contribuciones son bienvenidas! Por favor, sigue el flujo de trabajo estÃ¡ndar de GitHub (fork, feature branch, pull request).

## Licencia

Este proyecto estÃ¡ bajo la licencia MIT. Consulta el archivo LICENSE para mÃ¡s detalles.