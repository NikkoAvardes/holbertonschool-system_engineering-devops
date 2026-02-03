# 🏗️ Conception d'Infrastructure Web

Ce projet présente l'évolution d'une architecture web, de la plus simple à la plus robuste et scalable. Chaque diagramme illustre les composants clés, leur rôle et les interactions entre eux.

---

## 📋 Table des Matières

1. [Simple Web Stack](#1-simple-web-stack)
2. [Infrastructure Web Distribuée](#2-infrastructure-web-distribuée)
3. [Infrastructure Sécurisée et Monitorée](#3-infrastructure-sécurisée-et-monitorée)
4. [Scale Up](#4-scale-up)

---

## 1. Simple Web Stack

![Simple Web Stack](0-simple_web_stack.png)

### 📝 Description

Une infrastructure web basique hébergée sur un seul serveur. Cette configuration représente le point de départ le plus simple pour héberger un site web.

### 🔧 Composants

- **Serveur** : Un seul serveur (8.8.8.8) hébergeant tous les services
- **Nom de domaine** : www.foobar.com pointant vers le serveur
- **Serveur Web** : Nginx gérant les requêtes HTTP/HTTPS
- **Serveur d'Application** : Traitement de la logique métier
- **Base de données** : MySQL pour le stockage des données
- **Code Base** : L'application déployée sur le serveur

### ⚠️ Limitations

- **SPOF (Single Point of Failure)** : Si le serveur tombe, tout le site est inaccessible
- **Temps d'arrêt** : La maintenance nécessite l'arrêt du service
- **Scalabilité limitée** : Impossible de gérer un trafic important

---

## 2. Infrastructure Web Distribuée

![Infrastructure Web Distribuée](1-distributed_web_infrastructure.png)

### 📝 Description

Une infrastructure améliorée avec plusieurs serveurs pour répartir la charge et améliorer la disponibilité.

### 🔧 Composants

- **Load Balancer (HAProxy)** : Répartit le trafic entre plusieurs serveurs
- **Serveurs Web multiples** : Plusieurs instances pour gérer plus de requêtes
- **Serveur d'Application** : Logique métier séparée
- **Base de données** : Configuration Primary-Replica pour la redondance
  - **Primary (Master)** : Gère les écritures
  - **Replica (Slave)** : Gère les lectures et sert de backup

### ✅ Avantages

- Meilleure répartition de la charge
- Redondance des serveurs
- Amélioration de la disponibilité

### ⚠️ Limitations

- Pas de chiffrement des données
- Absence de monitoring
- Pas de pare-feu

---

## 3. Infrastructure Sécurisée et Monitorée

![Infrastructure Sécurisée et Monitorée](2-secured_and_monitored_web_infrastructure.png)

### 📝 Description

Une infrastructure complète avec sécurité renforcée et système de monitoring pour garantir la disponibilité et la protection des données.

### 🔧 Composants

#### Sécurité
- **Pare-feu (Firewall)** : 3 firewalls pour filtrer le trafic
- **Certificat SSL** : Chiffrement HTTPS pour sécuriser les communications
- **Protection DDoS** : Prévention des attaques par déni de service

#### Monitoring
- **Clients de Monitoring** : 3 clients collectant les métriques
- **Sumologic** : Agrégation et analyse des logs
- **Alertes** : Notification en cas de problèmes

#### Infrastructure
- **Load Balancer SSL** : Terminaison SSL au niveau du load balancer
- **Serveurs Web** : Distribution du trafic HTTPS
- **Base de données sécurisée** : Accès restreint et chiffré

### ✅ Avantages

- **Sécurité** : Chiffrement, pare-feu, protection contre les attaques
- **Monitoring** : Visibilité complète sur l'état du système
- **Conformité** : Respect des standards de sécurité (SSL/TLS)
- **Traçabilité** : Logs centralisés pour audit

### 📊 Métriques Monitorées

- Disponibilité des serveurs
- Temps de réponse
- Trafic réseau
- Utilisation CPU/RAM
- Requêtes par seconde (QPS)
- Erreurs et exceptions

---

## 4. Scale Up

![Scale Up](3-scale_up.png)

### 📝 Description

Architecture hautement scalable avec séparation des préoccupations et redondance complète. Chaque composant est dédupliqué pour éliminer les SPOF.

### 🔧 Composants

#### Load Balancing en Cluster
- **2 Load Balancers (HAProxy)** : Configuration active-active ou active-passive
- Élimination du SPOF au niveau du load balancing

#### Séparation des Services
- **Serveur Web dédié** : Uniquement pour servir le contenu statique et gérer HTTP/HTTPS
- **Serveur d'Application dédié** : Uniquement pour la logique métier
- **Serveur de Base de Données dédié** : Uniquement pour le stockage des données

### ✅ Avantages

- **Élimination des SPOF** : Redondance à tous les niveaux
- **Scalabilité horizontale** : Ajout facile de nouveaux serveurs
- **Isolation des services** : Meilleure maintenabilité et débogage
- **Performance optimale** : Chaque serveur optimisé pour sa tâche
- **Haute disponibilité** : Service continu même en cas de panne d'un composant

### 🚀 Évolutivité

Cette architecture permet de :
- Ajouter des serveurs web supplémentaires pour gérer plus de trafic
- Scaler les serveurs d'application indépendamment
- Mettre en place des réplicas de base de données supplémentaires
- Implémenter du caching (Redis, Memcached)
- Déployer dans plusieurs zones géographiques

---

## 📚 Concepts Clés

### Load Balancer
Répartit le trafic entrant entre plusieurs serveurs pour optimiser l'utilisation des ressources et éviter la surcharge.

### Primary-Replica Database
- **Primary** : Serveur principal gérant les écritures
- **Replica** : Copie du primary gérant les lectures et servant de backup

### SSL/TLS
Protocole de sécurité qui chiffre les communications entre le client et le serveur.

### Monitoring
Surveillance continue de l'infrastructure pour détecter et résoudre rapidement les problèmes.

### Firewall
Filtre le trafic réseau selon des règles de sécurité prédéfinies.

---

## 🎯 Objectifs du Projet

- Comprendre l'évolution d'une architecture web
- Identifier les SPOF et les éliminer
- Implémenter la sécurité à plusieurs niveaux
- Assurer la scalabilité et la haute disponibilité
- Mettre en place un monitoring efficace

---

## 👨‍💻 Auteur

Projet réalisé dans le cadre du cursus Holberton School - System Engineering & DevOps

---

## 📄 Licence

Ce projet est destiné à des fins éducatives.