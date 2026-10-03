# 🌴 Tourism Application

A **microservices-based tourism booking platform** built with **Spring Boot, Spring Cloud Gateway, React, MySQL, Docker, and Docker Compose**. 🚀

## 🏗️ Architecture

This repository contains a multi-module application with the following components:

* 🔐 `Backend/auth-service` – Authentication service with JWT support
* 📅 `Backend/booking-service` – Booking management service
* 📍 `Backend/destination-service` – Destination management service
* 🎒 `Backend/packages-service` – Travel package management service
* 🌐 `Backend/api-gateway` – Spring Cloud Gateway routing all API traffic through a single entry point
* 💻 `Frontend` – React frontend that consumes the API gateway
* 🗄️ `mysql-init` – MySQL initialization scripts for database bootstrapping

## 🛠️ Technology Stack

* ☕ Java 17
* 🍃 Spring Boot 3.x
* 🌐 Spring Cloud Gateway
* 🗃️ Spring Data JPA
* 🐬 MySQL 8
* 🔄 Flyway Migrations
* ⚛️ React 18
* 🐳 Docker & Docker Compose
* 🔑 JWT Authentication

## 🔌 Ports

| Service                |   Port |
| ---------------------- | -----: |
| 🌐 API Gateway         | `8080` |
| 🔐 Auth Service        | `8081` |
| 📅 Booking Service     | `8082` |
| 📍 Destination Service | `8083` |
| 🎒 Packages Service    | `8084` |
| 💻 Frontend            | `3000` |
| 🐬 MySQL               | `3306` |

## 🚀 Getting Started

### 📋 Prerequisites

Make sure you have the following installed:

* 🐳 Docker
* 🐳 Docker Compose
* ☕ Java 17
* 🟢 Node.js and npm

### 🐳 Run with Docker Compose

From the repository root:

```bash
docker compose up --build
```

This will build and launch:

* 🐬 MySQL
* 🔐 Auth Service
* 📅 Booking Service
* 📍 Destination Service
* 🎒 Packages Service
* 🌐 API Gateway
* 💻 Frontend

### 🚀 Run Production Compose

```bash
docker compose -f docker-compose.prod.yml up --build
```

## 🔐 Environment Configuration

Create and configure your environment variables before running the application.

Example:

```env
MYSQL_ROOT_PASSWORD=YOUR_STRONG_PASSWORD
JWT_SECRET=YOUR_LONG_RANDOM_SECRET
```

⚠️ **Never commit real passwords, API keys, JWT secrets, or other sensitive credentials to GitHub.**

## 💻 Local Development

### ☕ Backend Services

Each backend service is a separate Spring Boot application.

Example — Auth Service:

```bash
cd Backend/auth-service
./mvnw spring-boot:run
```

On Windows:

```cmd
cd Backend\auth-service
.\mvnw.cmd spring-boot:run
```

Repeat the process for:

* 🔐 `auth-service`
* 📅 `booking-service`
* 📍 `destination-service`
* 🎒 `packages-service`
* 🌐 `api-gateway`

### ⚛️ Frontend

Navigate to the frontend directory:

```bash
cd Frontend
npm install
npm start
```

To create a production build:

```bash
npm run build
```

## 🌐 Service Endpoints

The frontend communicates with the API Gateway through:

```text
http://localhost:8080
```

The API Gateway routes requests to the appropriate backend services:

| Route                     | Service             |
| ------------------------- | ------------------- |
| 🔐 `/api/auth/**`         | Auth Service        |
| 📅 `/api/bookings/**`     | Booking Service     |
| 📍 `/api/destinations/**` | Destination Service |
| 🎒 `/api/packages/**`     | Packages Service    |

## 🗄️ Database Initialization

MySQL is initialized using:

```text
mysql-init/init.sql
```

If you make changes to the initialization scripts, recreate the MySQL container:

```bash
docker compose down
docker compose up --build
```

## 🧪 Build & Test

### ☕ Backend

Compile a backend service:

```bash
cd Backend/auth-service
./mvnw compile
```

Run tests:

```bash
./mvnw test
```

### ⚛️ Frontend

```bash
cd Frontend
npm test
```

## 📝 Notes

* 🌐 The `api-gateway` provides a common entry point for the frontend and handles routing to backend microservices.
* ⚛️ The React application is built using `react-scripts`.
* 🐳 The frontend is served through Docker/Nginx on port `3000`.
* 🛑 Use the following command to stop the application stack:

```bash
docker compose down
```

## 🔧 Troubleshooting

### ⚠️ Ports Already in Use

If a port is already being used, stop the conflicting service or update the port mappings in `docker-compose.yml`.

### 🐬 MySQL Fails to Start

Check that:

* Port `3306` is available.
* The MySQL configuration is correct.
* The configured root password matches your environment configuration.

### 🔌 Backend Cannot Connect to MySQL

Make sure:

* 🐬 The MySQL container is running.
* 🌐 The backend services have access to the Docker network.
* 🔐 The database credentials are correctly configured.

## 👥 Project

This is a **group project** developed as part of our software engineering work, involving frontend development, backend microservices, database integration, authentication, and containerization.
