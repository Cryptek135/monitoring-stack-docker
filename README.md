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
Lancer les services :

Bash

sudo docker compose up -d
L'interface est désormais accessible sur http://localhost (ou l'IP du serveur).

🔒 Sécurité et Optimisation
Isolation réseau : Accès direct à Netdata désactivé, tout trafic passe par Nginx.

Défense périmétrique : Configuration de Fail2Ban pour détecter les scans de vulnérabilités sur le port 80.

Persistance des données : Utilisation de volumes Docker pour conserver les configurations d'alertes Discord.

Accès restreint : Montage des répertoires sensibles (/proc, /sys) en mode Lecture Seule (ReadOnly).

🚨 Cas d'usage : Détection d'incident réel
Lors des tests, le système a permis de détecter une saturation critique du disque :

NOTIF DISCORD : mon-serveur-netdata is critical, Disk / space usage = 99%

🧠 Compétences acquises
Administration de serveurs Linux et gestion des services (Systemd).

Maîtrise de la conteneurisation avec Docker et Docker Compose.

Mise en œuvre de stratégies de sécurité (Reverse Proxy, IDS/IPS avec Fail2Ban).

Monitoring et Observabilité (Gestion des seuils d'alerte et Webhooks).
