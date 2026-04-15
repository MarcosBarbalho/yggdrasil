<img src=".github/img/ygginha.png" width="128px" height="128px" align="left"/>

# Ygginha

Infrastructure based on docker-compose to run services locally using Docker.

## Requirements

To properly run Ygginha on your system, make sure you have the following installed:

- docker: https://www.docker.com/
- docker-compose: https://docs.docker.com/compose/ (prefer installing the plugin version if not already installed)
- openssl: https://www.openssl.org/ (only required for generating new self-signed certificates)

## Steps

With Ygginha cloned to your machine, follow the steps below from the project root to get everything running:

1) Configure the networks on your system
    1) `docker network create web`
    2) `docker network create database`
2) Run `docker compose up -d` to start the base services
3) Start any additional services as needed

## Components

This project includes the following components:

- Traefik v2.10
- Adminer v4
- PostgreSQL v14.7
- Redis v7
- phpRedisAdmin v1.19
- mailpit v1.9

### Traefik

Traefik provides a dashboard where you can visualize all configured backends and frontends.

This interface is available at: http://127.0.0.1:8080

#### Self-signed certificate generation

If you need to generate a new certificate, use the command below:

```bash
openssl req \
-x509 \
-newkey rsa:2048 \
-keyout ./cert/key.key \
-out ./cert/cer.crt \
-days 3560 \
-nodes \
-subj "/C=BR/ST=Minas Gerais/L=Betim/O=Ygginha LTDA./OU=Tech/CN=localhost" \
-addext "subjectAltName=DNS:*.localhost"
```

## Recommended Reading

For a better understanding of this setup, it is recommended to research any unfamiliar technical terms, especially related to:

- docker: https://www.docker.com/
- docker-compose: https://docs.docker.com/compose/
