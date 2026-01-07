# 📱 Application de Gestion de Salles par QR Code

## 📌 Contexte du Projet
Ce projet consiste à développer une application web et mobile permettant la **gestion de salles via des QR codes**.  
Chaque salle dispose d’un **QR code unique**, automatiquement **régénéré chaque semaine**, permettant de consulter en temps réel la disponibilité et le planning associé.

L’objectif est de faciliter l’accès aux informations de réservation et d’occupation des salles via un simple scan.

---

## 🎯 Objectifs Principaux
- Générer des **QR codes uniques par salle**, renouvelés automatiquement chaque semaine
- Afficher un **planning dynamique** de disponibilité des salles
- Visualiser la **liste des salles** avec leurs QR codes associés
- Automatiser la génération des QR codes selon un **calendrier hebdomadaire**

---

## 🗄️ Structure de la Base de Données

### 📘 Table : `Salles`
| Champ | Type | Description |
|------|------|-------------|
| nom_salle | TEXT (UNIQUE) | Identifiant unique de la salle |
| promo | TEXT | Promotion / cursus associé |
| class | TEXT | Classe ou groupe |
| qr_code | TEXT / BLOB | QR code généré pour la semaine |
| date_debut | DATE | Début de validité du planning |
| heure_debut | TIME | Heure de disponibilité |
| date_fin | DATE | Fin de validité du planning |
| heure_fin | TIME | Heure de fin de disponibilité |
| date_creation_qr | TIMESTAMP | Date de génération du QR code |

### 📗 Table : `Planning` (optionnelle)
| Champ | Type | Description |
|------|------|-------------|
| id_planning | PRIMARY KEY | Identifiant du planning |
| id_salle | FOREIGN KEY | Référence à la salle |
| semaine | DATE | Semaine concernée |
| creneau | TIME RANGE | Plage horaire |
| disponibilite | BOOLEAN | Libre / Occupée |

---

## ⚙️ Fonctionnalités Attendues

### 1️⃣ Génération Automatique des QR Codes
- Génération hebdomadaire (ex : chaque lundi)
- Contenu du QR code :
  - Nom de la salle
  - Semaine en cours
  - Hash de sécurité
- Stockage du QR code en base de données
- Conservation de l’**historique des QR codes**

---

### 2️⃣ Affichage du Planning
Pour chaque salle :
- Nom de la salle
- Promo et classe associées
- Statut actuel : **Disponible / Occupée**
- Horaires de la semaine en cours
- QR code affiché et téléchargeable

---

### 3️⃣ Scannage du QR Code
Après scan :
- Redirection vers une page dédiée
- Informations affichées :
  - Nom de la salle
  - Planning détaillé (jour par jour, heure par heure)
  - Disponibilité en temps réel
  - Prochains créneaux disponibles

---

### 4️⃣ Interface Administrative
- Gestion manuelle des salles
- Paramétrage du jour et de l’heure de génération des QR codes
- Visualisation du planning global
- Régénération manuelle d’un QR code si nécessaire
- Accès sécurisé (authentification administrateur)

---

## 🧩 Spécifications Techniques

### 🔙 Backend
- API REST pour la gestion des salles et du planning
- Service de génération de QR codes
- Tâche planifiée (CRON) pour la génération hebdomadaire
- Authentification administrateur

### 🔜 Frontend
- Interface responsive (Web & Mobile)
- Affichage dynamique du planning
- Scanner de QR code intégré
- Mise à jour des données en temps réel

---

## 🛠️ Stack Recommandée

### Backend
- Node.js / Express  
- Python / Flask  

### Base de Données
- PhpMyAdmin
- MySQL  
- MongoDB  

### QR Code
- `qrcode.js`
- `python-qrcode`
- Librairie équivalente

### Scheduling
- `node-cron`
- APScheduler
- Laravel Task Scheduler

### Frontend
- HTML
- CSS
- JS

---

## ✅ Points Clés à Respecter
- ✅ QR code unique par salle et par semaine  
- ✅ Génération automatique sans intervention manuelle  
- ✅ Historique des QR codes conservé  
- ✅ Planning fiable et à jour  
- ✅ Interface intuitive et rapide  
- ✅ Accès via scanner mobile  
- ✅ Sécurité des données de planning  

---

## 📦 Livrables Attendus
- Application fonctionnelle de gestion de salles
- Système automatique de génération de QR codes
- Interface d’affichage du planning
- Documentation technique et utilisateur
- Tests unitaires et d’intégration
