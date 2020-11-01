# Strapi application

A quick description of your strapi application

## Local development

The most convenient way how to run Strapi locally is to use docker.

### Installation

1. create `my-project-api` folder
1. move in and create `docker-compose.yaml` with:

```
version: '3'
services:
  strapi:
    image: strapi/strapi
    environment:
      DATABASE_CLIENT: postgres
      DATABASE_NAME: strapi
      DATABASE_HOST: postgres
      DATABASE_PORT: 5432
      DATABASE_USERNAME: strapi
      DATABASE_PASSWORD: strapi
    volumes:
      - ./app:/srv/app
    ports:
      - '1337:1337'
    depends_on:
      - postgres

  postgres:
    image: postgres
    environment:
      POSTGRES_DB: strapi
      POSTGRES_USER: strapi
      POSTGRES_PASSWORD: strapi
    volumes:
      - ./data:/var/lib/postgresql/data
```

1. clone Github repository into name `app` folder - `git clone git@github.com:msmid/nextrapi-api.git app`
1. start Docker with `docker-compose up -d`

You can use different docker image if you, for example, rather use mongodb. See https://strapi.io/documentation/v3.x/installation/docker.html

For other docker images, visit https://hub.docker.com/r/strapi/strapi

## Development

1. Copy `.env.example` into `.env` and configure it for local development
1. Start docker with `docker-compose up -d` (or with Docker Desktop)
1. Strapi is running on `http://localhost:1337`, graphql on `http://localhost:1337/graphql`