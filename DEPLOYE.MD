# Train Food Ordering System - Deployment Guide

This guide explains how to deploy the application on any machine using Docker or Podman.

## Pre-requisites
- [Git](https://git-scm.com/)
- [Docker & Docker Compose](https://www.docker.com/) OR [Podman & Podman Compose](https://podman.io/)

## Quick Start (Docker)

1.  **Clone the Repository**
    ```bash
    git clone https://github.com/NimanthaFernando/train-food-ordering-webapp.git
    cd train-food-ordering-webapp
    ```

2.  **Setup Environment**
    Copy the example configuration to a real configuration file:
    ```bash
    cp .env.example .env
    ```

3.  **Start Containers**
    Build and start the application in the background:
    ```bash
    docker-compose up -d --build
    ```

4.  **Install Dependencies**
    Install PHP dependencies inside the container:
    ```bash
    docker-compose exec app composer install
    ```

5.  **Initialize Application**
    Generate the encryption key and run database migrations:
    ```bash
    docker-compose exec app php artisan key:generate
    docker-compose exec app php artisan migrate --seed
    ```

6.  **Access the App**
    - Application: [http://localhost:8000](http://localhost:8000)
    - Database Admin (phpMyAdmin): [http://localhost:8081](http://localhost:8081)

---

## Quick Start (CentOS / Podman)

If you are on CentOS/RHEL using Podman:

1.  **Clone the Repository**
    ```bash
    git clone https://github.com/NimanthaFernando/train-food-ordering-system.git
    cd train-food-ordering-webapp
    ```

2.  **Run Setup Script**
    We have included a setup script specifically for CentOS/Podman environments:
    ```bash
    chmod +x setup.sh
    ./setup.sh
    ```
    This script will automatically handle `.env` creation, container startup, and permissions.
