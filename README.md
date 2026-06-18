#  Secure AWS Mini Lab

##  Objectif du projet
Déploiement d'une infrastructure cloud minimale sur AWS en appliquant de bout en bout les principes fondamentaux de la sécurité informatique (moindre privilège, isolation réseau et traçabilité).

##  Architecture & Sécurité implémentée

### 1. Gestion des Accès (IAM)
- **Compte Root sécurisé** et inutilisé pour les tâches quotidiennes.
- Création d'un utilisateur administrateur nommé `Ife`.
- **MFA (Multi-Factor Authentication)** activé obligatoirement via une application d'authentification.

### 2. Sécurité Réseau & Système (EC2 & UFW)
- Déploiement d'une instance virtuelle **Ubuntu Server 24.04 LTS**.
- Le **Security Group AWS** (pare-feu cloud) est restreint uniquement à mon adresse IP publique `/32` sur le port 22 (SSH).
- **Hardening OS** : Activation du pare-feu applicatif Linux `ufw` réglé sur `deny incoming` par défaut, autorisant uniquement `OpenSSH`.

### 3. Gouvernance & Audit
- Activation d'**AWS CloudTrail** pour enregistrer et auditer l'ensemble des appels API du compte.
- Stockage sécurisé des journaux de logs au sein d'un compartiment **Amazon S3** dédié.
