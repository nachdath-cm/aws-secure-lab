#  Secure AWS Mini Lab

##  Objectif du projet
Déploiement d'une infrastructure cloud minimale sur Amazon Web Services (AWS) en appliquant de bout en bout les principes fondamentaux de la sécurité informatique : le moindre privilège, l'isolation réseau, le durcissement système et la traçabilité.

---

## 🛡️ Architecture & Sécurité implémentée

### 1. Gestion des Accès (IAM)
* **Principe appliqué** : Isolation du compte racine (Root) et authentification forte.
* **Actions** : Création d'un groupe d'administration `AdminGroup` associé à la politique `AdministratorAccess`. Liaison de l'utilisateur personnalisé `Ife`. Activation obligatoire de l'authentification multi-facteur (MFA).

#### 📸 Preuve de configuration IAM & MFA :

![IAM User & MFA Status]()

---

### 2. Isolation Réseau & Sécurité Périmétrique (VPC / Security Groups)
* **Principe appliqué** : Réduction drastique de la surface d'attaque externe.
* **Actions** : Configuration des règles de pare-feu au niveau du Cloud (*Security Group*). Blocage complet de tous les flux entrants génériques (`0.0.0.0/0`). Restriction stricte du port SSH (22) à mon adresse IP publique unique (`/32`).

#### 📸 Preuve du Security Group AWS :
![AWS Security Group Restricted IP]()

---

### 3. Durcissement Système (Linux OS Hardening)
* **Principe appliqué** : Défense en profondeur au niveau de l'hôte.
* **Actions** : Déploiement d'une instance virtuelle **Ubuntu Server**. Mise à jour complète des paquets de sécurité critiques (`apt upgrade`). Configuration et activation du pare-feu applicatif interne `ufw` réglé sur un blocage total par défaut (`deny incoming`) avec exception unique pour `OpenSSH`.

#### 📸 Preuve du statut du pare-feu Linux :
![Linux UFW Status Active]()

---

### 4. Traçabilité, Audit & Surveillance (CloudTrail & S3)
* **Principe appliqué** : Immutabilité des journaux de logs et audit permanent.
* **Actions** : Activation globale d'**AWS CloudTrail** pour capturer 100 % des appels d'API et des actions menées sur l'infrastructure. Exportation et centralisation automatique de ces journaux vers un compartiment de stockage **Amazon S3** (`aws-secure-lab-logs-ife`) chiffré par défaut.

#### 📸 Preuve de l'activation des logs :
![AWS CloudTrail & S3 Bucket]()
