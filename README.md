# Docker

## Objectif

Le but est de pousser vos connaissances le plus loin possible. Voici de quoi faire mais si vous voulez ajouter des choses pour plus de bonheur, go !
Force et honneur.

### Très simple

Conteneuriser une application web dans un dockerfile. Pouvoir le build et le lancer facilement

### Simple

Reprendre l'app web et le dockerfile précedent, l'utiliser dans un docker compose et ajouter une appli backend

### Moyen

Reprendre toutes la stack précedente pour y greffer une base de donnée. Le contenu de la base de donnée persistent même après avoir relancer le docker compose
Le backend doit avoir accès a la base de donnée mais pas le frontend (bloquage niveau network)

## Documentation

# Docker Project Documentation

## Vue d'ensemble

Ce projet est une application web moderne construite avec Next.js, utilisant une architecture en microservices avec Docker. Il comprend un frontend, un backend et une base de données PostgreSQL.

## Technologies Utilisées

### Frontend (app/)

- Next.js 15.1.4
- React 19
- TypeScript
- TailwindCSS
- Docker

### Base de Données

- PostgreSQL 17

## Configuration Docker

### Production

Le fichier `docker-compose.yml` définit l'environnement de production avec :

- Frontend Next.js (port 3000)
- Base de données PostgreSQL
- Réseau isolé "backend"
- Volumes persistants pour PostgreSQL

### Développement Local

Le fichier `docker-compose.local.yml` est optimisé pour le développement avec :

- Base de données PostgreSQL exposée sur le port 5432
- Volumes persistants pour les données

## Commandes Make

### Démarrer l'environnement local

```bash
make up
```

### Arrêter l'environnement local

```bash
make down
```

## Configuration Frontend

L'application Next.js est configurée avec :

- Mode standalone pour l'optimisation Docker
- Support TypeScript
- Tailwind CSS pour le styling
- Polices Geist (Sans et Mono)
- Configuration ESLint personnalisée

## Variables d'Environnement

Un fichier `.env` est requis à la racine du projet pour la configuration de PostgreSQL. Les variables nécessaires sont :

- Variables de configuration PostgreSQL (à définir selon vos besoins)

## Réseaux Docker

Le projet utilise un réseau bridge nommé "backend" pour isoler les communications entre les services.

## Volumes

- `postgres-data`: Volume persistant pour les données PostgreSQL

## Sécurité

- Isolation réseau entre les services
- Utilisateur non-root pour le conteneur Next.js
- Configuration sécurisée des conteneurs

## Démarrage Rapide

1. Cloner le repository
2. Créer un fichier `.env` avec les variables nécessaires
3. Exécuter `make up` pour démarrer l'environnement local
4. Accéder à l'application sur `http://localhost:3000`

## Développement

Pour le développement local :

1. Naviguer vers le dossier `app/`
2. Installer les dépendances : `npm install`
3. Lancer le serveur de développement : `npm run dev`
4. L'application sera disponible sur `http://localhost:3000`

## Build et Déploiement

Le build de l'application est automatisé via Docker avec plusieurs étapes :

1. Installation des dépendances
2. Build de l'application Next.js
3. Configuration de l'environnement de production
4. Optimisation des assets et du bundle

## Notes Importantes

- L'application utilise le mode standalone de Next.js pour une meilleure optimisation Docker
- Les données PostgreSQL sont persistantes grâce aux volumes Docker
- Le frontend et la base de données sont isolés via le réseau Docker
