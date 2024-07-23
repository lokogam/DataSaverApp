
# DataSaverApp

DataSaverApp is an application developed with Laravel that allows users to efficiently manage and save data. This project uses Docker to facilitate its deployment and configuration.

## Installation

Follow these steps to clone and install the project:

### Clone the project

Clone the repository from GitHub:

```bash
git clone https://github.com/lokogam/DataSaverApp.git
cd DataSaverApp
```

## Requirements

Make sure you have the following requirements installed on your machine:

- Docker
- Docker Compose

## Environment Configuration

Copy the example configuration file and update the environment variables as needed:

```bash
cp .env.example .env
```

## Installing Dependencies

Use Docker to install the project's dependencies with Composer:

```bash
docker run --rm \
    -u "$(id -u):$(id -g)" \
    -v "$(pwd):/var/www/html" \
    -w /var/www/html \
    laravelsail/php83-composer:latest \
    composer install --ignore-platform-reqs
```

## Bringing up the services

Use Docker Compose to bring up the services needed for the project:

```bash
./vendor/bin/sail up
```

## Migrating the database

Run the migrations to set up the database:

```bash
./vendor/bin/sail artisan migrate
```

## Installing and building the frontend assets

Install the npm dependencies and build the assets:

```bash
./vendor/bin/sail npm install
./vendor/bin/sail npm run build
```

## Accessing the application

The application will be available at http://localhost
