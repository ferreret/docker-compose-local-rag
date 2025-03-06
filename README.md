# 🐳 Docker Compose Configuration for n8n, Postgres, pgAdmin, Ollama, Open WebUI, and Qdrant

This repository contains a `docker-compose.yml` file that sets up a development environment with the following services:

## 🚀 Services

### 1. **n8n** 🤖
- **Image**: `docker.n8n.io/n8nio/n8n`
- **Port**: `5678:5678`
- **Volumes**: `n8n_data:/home/node/.n8n`
- **Network**: `my_network`
- **Description**: n8n is an open-source workflow automation tool. It allows you to connect different apps and services to automate tasks.

### 2. **Postgres** 🐘
- **Image**: `postgres`
- **Port**: `5432:5432`
- **Environment**:
  - `POSTGRES_USER=admin`
  - `POSTGRES_PASSWORD=74.Bizcochito`
- **Healthcheck**: Ensures the database is ready before accepting connections.
- **Volumes**: `postgres_data:/var/lib/postgresql/data`
- **Network**: `my_network`
- **Description**: PostgreSQL is a powerful, open-source relational database system.

### 3. **pgAdmin** 🛠️
- **Image**: `dpage/pgadmin4`
- **Port**: `90:80`
- **Environment**:
  - `PGADMIN_DEFAULT_EMAIL=aitecnomedia@oficinasinpapel.com`
  - `PGADMIN_DEFAULT_PASSWORD=74.Heladito`
- **Volumes**: `pgadmin_data:/var/lib/pgadmin`
- **Depends on**: `postgres`
- **Network**: `my_network`
- **Description**: pgAdmin is a web-based administration tool for PostgreSQL.

### 4. **Ollama** 🦙
- **Image**: `ollama/ollama`
- **Port**: `11434:11434`
- **Volumes**: `ollama_data:/root/.ollama`
- **Network**: `my_network`
- **Description**: Ollama is a tool for managing and running machine learning models.

### 5. **Open WebUI** 🌐
- **Image**: `ghcr.io/open-webui/open-webui:main`
- **Port**: `3000:8080`
- **Volumes**: `open-webui_data:/app/backend/data`
- **Environment**:
  - `OLLAMA_BASE_URL=http://ollama:11434`
- **Network**: `my_network`
- **Description**: Open WebUI provides a user-friendly interface for interacting with Ollama.

### 6. **Qdrant** 🗂️
- **Image**: `qdrant/qdrant`
- **Ports**:
  - `6333:6333`
  - `6334:6334`
- **Volumes**: `qdrant_data:/qdrant/storage`
- **Network**: `my_network`
- **Description**: Qdrant is a vector search engine that allows you to store, search, and manage vectors.

## 🌐 Networks
- **my_network**: A bridge network that connects all the services.

## 💾 Volumes
- **n8n_data**: Stores n8n data.
- **postgres_data**: Stores PostgreSQL data.
- **pgadmin_data**: Stores pgAdmin data.
- **ollama_data**: Stores Ollama data.
- **open-webui_data**: Stores Open WebUI data.
- **qdrant_data**: Stores Qdrant data.

## 🛠️ Usage
To start the services, run the following command:

```bash
docker compose up -d
```

To stop the services, run:

```bash
docker compose down
```

## 📝 Notes
- Ensure Docker and Docker Compose are installed on your system.
- Modify the environment variables as needed for your setup.