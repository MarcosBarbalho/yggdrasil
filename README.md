<img src=".github/img/ygginha.png" width="128px" height="128px" align="left"/>

# Ygginha

Infra baseada em [docker-compose][1] para rodar localmente os serviços via Docker.

## Requisitos

Para o correto funcionamento da Ygginha em seu sistema, é necessário ter instalado os seguintes componentes:

- [docker][2]
- [docker-compose][1] (instale preferencialmente o plugin, caso já não esteja instalado)
- [openssl](https://www.openssl.org/) (somente para a geração de novos certificados auto-assinados)

## Passos

Com a Ygginha clonada em seu computador, siga os passos abaixo, na raiz do projeto, para tê-la funcionando.

1) Configurar as networks no seu sistema
    1) `docker network create web`
    2) `docker network create database`
2) Executar o `docker compose up -d` para subir os serviços base
3) Subir cada serviço que precisar

## Componentes

Neste projeto estão inclusos os seguintes componentes:
- Traefik v2.10
- Adminer v4
- PostgreSQL v14.7
- Redis v7
- phpRedisAdmin v1.19
- mailpit v1.9

### Traefik

O Traefik possui uma interface onde é possível visualizar todos backends e frontends configurados nele.

Essa interface é acessível através da URL [http://127.0.0.1:8080](http://127.0.0.1:8080)

#### Geração de certificado auto-assinado

Caso seja necessário gerar um novo certificado, use o comando abaixo:

```bash
$ openssl req \
-x509 \
-newkey rsa:2048 \
-keyout ./cert/key.key \
-out ./cert/cer.crt \
-days 3560 \
-nodes \
-subj "/C=BR/ST=Minas Gerais/L=Betim/O=Ygginha LTDA./OU=Tech/CN=localhost" \
-addext "subjectAltName=DNS:*.localhost"
```

## Leitura recomendada

Para um melhor entendimento do que está acontecendo aqui, recomendo pesquisar sobre qualquer termo técnico que você desconheça, especialmente sobre [docker][2] e [docker-compose][1].

[1]: https://docs.docker.com/compose/
[2]: https://www.docker.com/

# ygginha
