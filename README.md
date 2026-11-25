# Déploiement d'une application MERN avec Docker

## Objectif
Conteneuriser une application MERN (MongoDB, Express, React, Node.js) avec Docker et Docker Compose.

## Étapes réalisées

1. Clonage : git clone https://github.com/wiem-kb/MyAppReact.git
2. Création des Dockerfiles (Server et Client) avec l'image node:lts-alpine.
3. Construction des images : docker build -t mern-server ./Server et docker build -t mern-client ./Client
4. Création du réseau : docker network create mern-network
5. Lancement de MongoDB, du serveur (port 9000) et du client (port 3000) avec docker run.
6. Création du docker-compose.yml (services mongodb, server, client, réseau mern-network en bridge, variable MONGO_URI).
7. Lancement : docker compose up --build

## Accès
- Client : http://localhost:3000
- Serveur : http://localhost:9000

## Arrêt
docker compose down
