# LEMP Docker

## Description
Lightweight LEMP (Linux, Nginx, MySQL/MariaDB, PHP-FPM) stack configured for local development using Docker Compose. Provides a reproducible environment for PHP applications with an isolated webserver, PHP runtime, and database.

## Requirements
- Docker Engine (recommended: latest stable)
- Docker Compose (or Docker CLI plugin `docker compose`)
- Git (to clone the repository)
- Minimum 2GB free RAM for containers
- Optional: .env file editor (text editor / VS Code)

## Installation
1. Clone the repository:
    ```
    git clone <repo-url> lemp-docker
    cd lemp-docker
    ```
2. Copy and configure environment:
    ```
    cp .env.example .env
    # Edit .env to set DB credentials, ports, etc.
    ```
3. Start services:
    ```
    docker compose up -d
    ```
4. Verify:
    - Web: http://localhost (or custom PORT in .env)
    - DB: connect to host `127.0.0.1` and configured port
5. Stop services:
    ```
    docker compose down
    ```

## Project structure
/
- docker-compose.yml                # Compose definition for nginx, php-fpm, db, etc.
- .env.example                      # Example environment variables
- README.md
- nginx/
  - Dockerfile
  - conf.d/
     - default.conf                   # Nginx site configuration
- php/
  - Dockerfile
  - php.ini
- db/
  - Dockerfile or my.cnf
  - initdb/                          # Optional database initialization scripts
- www/ or html/                      # Document root for your PHP application
- data/                              # Persistent volumes (db data, nginx logs)
- scripts/                           # Helper scripts (backups, migrations)




Notes:
- Keep secrets out of the repository; use .env and Docker secrets for sensitive data.
- Customize ports and volumes via .env or docker-compose.yml as needed.
- Add healthchecks and backups for production-like resilience.