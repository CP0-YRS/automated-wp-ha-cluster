# 🚀 Automated WordPress HA Cluster

Ce projet automatise le déploiement d'une infrastructure Web en **Haute Disponibilité (HA)**. Grâce à l'utilisation d'**Ansible** et **Docker**, l'ensemble de l'architecture est déployé de manière reproductible et résiliente.

## 🏗️ Architecture du Projet
L'infrastructure est composée de 4 serveurs Linux (Ubuntu) :

1.  **Load Balancer (Nginx) :** IP `.160` - Répartit le trafic vers les serveurs Web et gère le failover.
2.  **Web Server 1 (WordPress/Docker) :** IP `.159` - Premier nœud d'application.
3.  **Web Server 2 (WordPress/Docker) :** IP `.161` - Second nœud d'application.
4.  **Database Server (MariaDB/Docker) :** IP `.171` - Serveur de données centralisé pour les deux nœuds Web.

## 🛠️ Stack Technique
- **Orchestration :** Ansible (Playbooks YAML)
- **Conteneurisation :** Docker & Docker Compose
- **Serveur Web & Proxy :** Nginx
- **Application :** WordPress
- **Base de données :** MariaDB

## 🌟 Fonctionnalités clés
- **Automatisation complète :** Déploiement de la base de données et du cluster WordPress en deux commandes Ansible.
- **Résilience (HA) :** Le site reste accessible même si l'un des deux serveurs Web tombe en panne (testé et validé).
- **Centralisation des données :** Utilisation d'une base de données externe pour permettre aux nœuds Web d'être interchangeables.

## 🚀 Comment l'utiliser ?

1. Configurer l'inventaire dans le fichier `hosts.ini`.
2. Déployer la base de données :
   ```bash
   ansible-playbook -i hosts.ini deploy-db.yml
