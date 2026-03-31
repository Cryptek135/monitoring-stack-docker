# 📊 Stack de Monitoring Système Sécurisée (Netdata + Nginx + Fail2Ban)

## 🎯 Présentation du Projet
Infrastructure d'observabilité complète et durcie via **Docker**. Ce projet permet de surveiller un serveur en temps réel tout en protégeant l'accès aux métriques sensibles.

## 🏗️ Architecture & Sécurité
* **Collecte** : Netdata (métriques à la seconde).
* **Reverse Proxy** : Nginx (Centralisation port 80).
* **Authentification** : Basic Auth (Login/Password requis).
* **Protection Active** : Fail2Ban surveille les logs Nginx et bannit les tentatives d'intrusion.
* **Alerting** : Notifications critiques instantanées via **Discord Webhook**.

## 🧪 Validation du Système (Tests réels)
Le système a été validé par les tests suivants :
1. **Authentification** : Accès bloqué sans identifiants valides.
2. **Logs Persistants** : Vérification des tentatives de connexion via `cat logs/error.log`.
3. **Fail2Ban** : Détection des erreurs 401 et incrémentation du compteur de bannissement.
4. **Discord** : Réception d'alertes WARNING/CRITICAL via le script de test Netdata.

## 🧠 Compétences validées
* Orchestration Docker multi-services.
* Sécurisation d'applications web (Reverse Proxy + Auth).
* Gestion des logs et analyse de sécurité avec Fail2Ban.
* Intégration d'API tierces pour le monitoring proactif.
