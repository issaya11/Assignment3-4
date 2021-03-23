#below is the code that we inserted to fix this vulnerability

version: '2'

services:

  nginx:
    image: nginx:latest
    ports:
      - "80:80"
    volumes:
      - ./code:/code
      - ./site.conf:/etc/nginx/conf.d/site.conf
    links:
      - php

  php:
    build: 
      context: ./dockerfiles/php/
      dockerfile: ./Dockerfile
    volumes:
        - ./code:/code
    links:
      - db

  db:
    image: postgres:latest
    restart: always
    ports:
      - "5432:5432"
    volumes:
      - ./init-db.sh:/docker-entrypoint-initdb.d/init-db.sh
      - ./schema.sql:/schema.sql
      - ./data.sql:/data.sql
    environment:
      POSTGRES_PASSWORD: assignment1dbadmin

  adminer:
    image: adminer
    restart: always
    ports:
      - "8081:8080"
