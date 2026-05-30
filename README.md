# 🩺 SkinCheck — Plateforme de Détection du Cancer Cutané

![Python](https://img.shields.io/badge/Python-3.12-blue?style=flat-square&logo=python)
![Flask](https://img.shields.io/badge/Flask-2.x-black?style=flat-square&logo=flask)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange?style=flat-square&logo=tensorflow)
![MySQL](https://img.shields.io/badge/MySQL-8.0-blue?style=flat-square&logo=mysql)

---

## 📋 Description

**SkinCheck** est une application web médicale développée avec **Flask** (Python) intégrant un modèle de Deep Learning **VGG16** pour la détection automatique du cancer cutané.

L'application permet aux professionnels de santé de :
- Se connecter / s'inscrire de manière sécurisée
- Soumettre une image d'une lésion cutanée
- Obtenir un diagnostic automatique **Bénin** ou **Malin** avec un score de confiance
- Consulter l'historique complet des patients analysés

---

## 🖥️ Captures d'écran

### Page de Connexion
> Interface de connexion avec image médicale en arrière-plan et formulaire sur fond blanc

### Dashboard
> Tableau de bord avec statistiques en temps réel (total patients, cas malins, cas bénins)

### Page d'Analyse
> Formulaire de soumission d'image avec prévisualisation avant analyse

### Résultat du Diagnostic
> Affichage du diagnostic avec barre de confiance colorée (vert = bénin, rouge = malin)

### Historique Patients
> Tableau complet de tous les diagnostics enregistrés

---

## 🏗️ Architecture du Projet

```
DERMAI/
├── app.py                          # Application Flask principale
├── model/
│   └── vgg16_malignant_benign.h5  # Modèle VGG16 pré-entraîné
├── static/
│   ├── style.css                   # Feuille de styles principale
│   ├── medical_bg.jpg              # Image de fond médicale
│   └── uploads/                    # Images patients uploadées
└── templates/
    ├── login.html                  # Page de connexion
    ├── register.html               # Page d'inscription
    ├── dashboard.html              # Tableau de bord
    ├── predict.html                # Formulaire d'analyse
    ├── result.html                 # Résultat du diagnostic
    └── patients.html               # Historique des patients
```

---

## ⚙️ Prérequis

- Python 3.10 ou supérieur
- XAMPP (Apache + MySQL)
- pip

---

## 🚀 Installation & Lancement

### 1. Cloner le dépôt

```bash
git clone https://github.com/votre-username/SkinCheck.git
cd SkinCheck
```

### 2. Installer les dépendances Python

```bash
pip install flask tensorflow numpy mysql-connector-python
```

### 3. Configurer la base de données

- Ouvrir **XAMPP** et démarrer **Apache** + **MySQL**
- Aller sur `http://localhost/phpmyadmin`
- Exécuter le script SQL suivant :

```sql
CREATE DATABASE skin_cancer_db;
USE skin_cancer_db;

CREATE TABLE users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  username VARCHAR(50),
  password VARCHAR(50)
);

CREATE TABLE patients (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100),
  age INT,
  result VARCHAR(20),
  probability FLOAT,
  image_path VARCHAR(255),
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

INSERT INTO users (username, password) VALUES ('admin', '1234');
```

### 4. Placer le modèle

Copier le fichier `vgg16_malignant_benign.h5` dans le dossier `model/` :

```
DERMAI/model/vgg16_malignant_benign.h5
```

### 5. Lancer l'application

```bash
python app.py
```

### 6. Accéder au site

Ouvrir le navigateur et aller sur :

```
http://127.0.0.1:5000
```

---

## 🔐 Identifiants par défaut

| Champ | Valeur |
|-------|--------|
| Nom d'utilisateur | `admin` |
| Mot de passe | `1234` |

> Vous pouvez aussi créer un nouveau compte via la page **Inscription**.

---

## 🧠 Modèle utilisé

| Propriété | Valeur |
|-----------|--------|
| Architecture | VGG16 |
| Tâche | Classification binaire |
| Classes | Bénin / Malin |
| Format | `.h5` (Keras/TensorFlow) |
| Entrée | Image 224×224 pixels |

---

## 🛠️ Technologies utilisées

| Technologie | Rôle |
|-------------|------|
| **Python 3.12** | Langage principal |
| **Flask** | Framework web backend |
| **TensorFlow / Keras** | Chargement et inférence du modèle VGG16 |
| **MySQL** | Base de données des patients |
| **HTML / CSS** | Interface utilisateur |
| **Bootstrap (via CDN)** | Composants UI |

---

## 📌 Fonctionnalités

- [x] Authentification (Login / Logout)
- [x] Inscription de nouveaux médecins
- [x] Upload et analyse d'images cutanées
- [x] Diagnostic Bénin / Malin avec score de confiance
- [x] Historique des patients en base de données
- [x] Interface responsive et professionnelle
- [x] Protection des routes par session

---

## 👤 Auteur

Projet réalisé dans le cadre du module **Technologies Avancées — Web IA**

**Établissement :** ENSTAB  
**Année :** 2025–2026

---

## 📄 Licence

Ce projet est réalisé à des fins académiques uniquement.

