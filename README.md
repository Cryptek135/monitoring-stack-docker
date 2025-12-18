# 📊 Stack de Monitoring Système Sécurisée (Netdata + Nginx + Fail2Ban)

## 🎯 Présentation du Projet
Ce projet consiste en la mise en place d'une infrastructure d'observabilité complète et sécurisée via Docker. Il permet de surveiller en temps réel les ressources d'un serveur (CPU, RAM, Disque, Réseau) tout en protégeant l'accès aux données par un Reverse Proxy.

## 🏗️ Architecture Technique
L'infrastructure est découpée en plusieurs couches pour garantir performance et sécurité :
- **Monitoring** : [Netdata](https://www.netdata.cloud/) pour la collecte de métriques à la seconde près.
- **Reverse Proxy** : **Nginx** qui centralise les flux sur le port 80 et masque l'accès direct au port 19999.
- **Sécurité Active** : **Fail2Ban** (sur l'hôte) pour le bannissement automatique des tentatives d'intrusion via l'analyse des logs Nginx.
- **Alerting** : Intégration **Discord Webhook** pour recevoir des notifications critiques instantanées.



## 🛠️ Installation et Déploiement

### Prérequis
- Docker & Docker Compose
- Fail2Ban installé sur le système hôte

### Lancer la stack
1. Cloner le dépôt :
   ```bash
   git clone [https://github.com/Cryptek135/monitoring-stack-docker.git](https://github.com/Cryptek135/monitoring-stack-docker.git)
   cd monitoring-stack-docker

## 🌐 Accès à l'interface
L'interface de monitoring est désormais sécurisée et accessible uniquement via le reverse proxy :
* **URL** : `http://localhost` (ou l'IP de votre serveur)
* **Port** : 80 (Standard Web)

## 🔒 Sécurité et Optimisation
* **Isolation réseau** : Le port natif de Netdata (19999) est fermé à l'extérieur. Seul le conteneur Nginx peut communiquer avec lui en interne.
* **Défense périmétrique** : Fail2Ban surveille les logs Nginx et bannit automatiquement les IP effectuant des scans de vulnérabilités.
* **Accès restreint** : Les répertoires sensibles de l'hôte (`/proc`, `/sys`) sont montés en mode **ReadOnly** pour empêcher toute modification depuis le conteneur.

## 🚨 Cas d'usage : Détection d'incident réel
Lors de la phase de test, le système a prouvé son efficacité en détectant une saturation critique :
> **NOTIF DISCORD** : `mon-serveur-netdata is critical, Disk / space usage = 99%`



## 🧠 Compétences acquises
* **Administration Linux** : Gestion des services avec `systemctl` (Apache vs Nginx) et analyse de logs.
* **Conteneurisation** : Orchestration multi-services avec Docker Compose et gestion des volumes persistants.
* **Sécurité** : Mise en place d'un Reverse Proxy et d'un système de détection d'intrusion (IDS/IPS).
* **Monitoring** : Configuration de seuils d'alertes et intégration d'API tierces (Webhooks Discord).
