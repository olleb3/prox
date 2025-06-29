# prox
projet de connexion des professionnels

ProX - Plateforme de Demandes et Offres d'Emploi
Table des matières
# Introduction # Fonctionnalités # Structure de l'Application # Installation # Utilisation  # Technologies Utilisées # Contribution # Licence

# 1. Introduction
ProX est une plateforme web conçue pour faciliter la mise en relation entre les recruteurs et les demandeurs d'emploi. Elle permet aux entreprises de publier des offres d'emploi et aux candidats de soumettre leurs demandes, le tout dans une interface simple et intuitive.

# 2. Fonctionnalités
Gestion des Offres d'Emploi :

Publication, modification et suppression d'offres par les recruteurs.

Consultation des offres disponibles par les candidats.

Gestion des Demandes d'Emploi :

Soumission de candidatures par les demandeurs d'emploi.

Consultation des demandes soumises.

Authentification Utilisateur :

Inscription et connexion sécurisées pour les différents types d'utilisateurs (recruteurs, candidats).

Déconnexion sécurisée.

# 3. Structure de l'Application
L'architecture de ProX suit le modèle MVC (Modèle-Vue-Contrôleur), garantissant une bonne séparation des préoccupations et facilitant la maintenance et l'évolution du code.

ProX/                                  // Dossier racine de l'application "ProX". Contient tout le code et les ressources du projet.
├── assets/                            // Contient les fichiers statiques (CSS, JavaScript, images) pour l'interface utilisateur.
│   ├── css/                           // Fichiers CSS pour le style visuel de l'application.
│   ├── js/                            // Fichiers JavaScript pour les interactions dynamiques côté client.
│   └── images/                        // Images, icônes, logos utilisés dans l'application.
├── controllers/                       // Dossier des contrôleurs (partie "C" du modèle MVC). Gèrent la logique des requêtes utilisateurs.
│   ├── DemandesEmplois/               // Sous-dossier pour les contrôleurs liés aux demandes d'emploi.
│   │   └── DemandesEmploisController.php // Contrôleur principal pour les actions des demandes d'emploi (créer, lire, modifier, supprimer).
│   └── OffresEmplois/                 // Sous-dossier pour les contrôleurs liés aux offres d'emploi.
│       └── OffresEmploisController.php // Contrôleur principal pour les actions des offres d'emploi (créer, lire, modifier, supprimer).
├── includes/                          // Dossier pour les fichiers PHP inclus, souvent des fonctions utilitaires ou des configurations.
│   ├── DemandesEmplois/               // Sous-dossier pour les fonctions spécifiques aux demandes d'emploi.
│   │   └── DemandesEmploisFunctions.php // Fonctions auxiliaires ou de validation propres aux demandes d'emploi.
│   ├── OffresEmplois/                 // Sous-dossier pour les fonctions spécifiques aux offres d'emploi.
│   │   └── OffresEmploisFunctions.php // Fonctions auxiliaires ou de validation propres aux offres d'emploi.
│   └── config/                        // Sous-dossier pour les fichiers de configuration de l'application.
│       └── database.php               // Fichier de configuration pour la connexion à la base de données (identifiants, hôte, etc.).
│       └── app_config.php             // Fichier de configuration générale de l'application (URL de base, chemins, etc.).
├── models/                            // Dossier des modèles (partie "M" du modèle MVC). Gèrent la logique métier et l'interaction avec la base de données.
│   ├── DemandesEmplois/               // Sous-dossier pour les modèles des demandes d'emploi.
│   │   └── DemandeEmploi.php          // Classe modèle représentant une demande d'emploi. Contient les propriétés et les méthodes d'accès aux données.
│   └── OffresEmplois/                 // Sous-dossier pour les modèles des offres d'emploi.
│       └── OffreEmploi.php            // Classe modèle représentant une offre d'emploi. Contient les propriétés et les méthodes d'accès aux données.
├── sql/                               // Dossier pour les scripts SQL.
│   └── prox_database.sql              // Script SQL pour la création des tables de la base de données et les données initiales.
├── views/                             // Dossier des vues (partie "V" du modèle MVC). Contient le code HTML/PHP pour l'affichage à l'utilisateur.
│   ├── DemandesEmplois/               // Sous-dossier pour les vues des demandes d'emploi.
│   │   ├── create_demande.php         // Vue (formulaire) pour créer une nouvelle demande d'emploi.
│   │   ├── view_demande.php           // Vue pour afficher les détails d'une demande d'emploi spécifique.
│   │   └── list_demandes.php          // Vue pour afficher une liste de toutes les demandes d'emploi.
│   ├── OffresEmplois/                 // Sous-dossier pour les vues des offres d'emploi.
│   │   ├── create_offre.php           // Vue (formulaire) pour créer une nouvelle offre d'emploi.
│   │   ├── view_offre.php             // Vue pour afficher les détails d'une offre d'emploi spécifique.
│   │   └── list_offres.php            // Vue pour afficher une liste de toutes les offres d'emploi.
│   ├── auth/                          // Sous-dossier pour les vues d'authentification.
│   │   ├── login.php                  // Vue (formulaire) de connexion utilisateur.
│   │   └── register.php               // Vue (formulaire) d'inscription utilisateur.
│   └── partials/                      // Sous-dossier pour les éléments de vue réutilisables (parties de pages).
│       ├── header.php                 // Partie supérieure de la page (en-tête HTML, navigation) incluse sur toutes les pages.
│       └── footer.php                 // Partie inférieure de la page (pied de page) incluse sur toutes les pages.
├── autoload.php                       // Fichier responsable du chargement automatique des classes PHP. Essentiel pour éviter les `require` manuels.
├── index.php                          // Point d'entrée unique de l'application. Toutes les requêtes sont routées via ce fichier.
├── login.php                          // Fichier traitant la logique et l'affichage de la connexion des utilisateurs.
├── logout.php                         // Fichier traitant la déconnexion des utilisateurs.
├── register.php                       // Enregistrer les utilisateurs
└── readme.md                          // Fichier Markdown contenant la description du projet, les instructions d'installation et d'utilisation.
# 4. Installation
Pour installer et faire fonctionner ProX sur votre machine locale, suivez les étapes ci-dessous :

Prérequis :

Serveur web (Apache, Nginx)

PHP 7.4 ou supérieur

MySQL ou compatible

Cloner le dépôt :

Bash

git clone [URL_DE_VOTRE_DEPOT] prox
cd prox
Configuration de la base de données :

Créez une base de données MySQL nommée prox_db (ou tout autre nom de votre choix).

Importez le schéma de la base de données à l'aide du fichier sql/prox_database.sql :

Bash

mysql -u votre_utilisateur -p prox_db < sql/prox_database.sql
Modifiez le fichier includes/config/database.php avec vos propres informations de connexion à la base de données.

Configuration de l'application :

Modifiez le fichier includes/config/app_config.php pour ajuster les paramètres généraux (ex: URL de base de l'application).

Serveur web :

Configurez votre serveur web (Apache/Nginx) pour pointer le document root vers le dossier ProX/.

# 5. Utilisation
Une fois l'installation terminée, ouvrez votre navigateur et accédez à l'URL configurée (par exemple, http://localhost/prox).

Utilisez les liens login.php et register.php pour gérer l'accès des utilisateurs.

L'index.php servira de point de départ pour la navigation principale.

# 6. Technologies Utilisées
Backend : PHP 7.4+

Base de Données : MySQL

Frontend : HTML5, CSS3, JavaScript

Architecture : MVC

# 7. Contribution
Nous encourageons les contributions à ProX ! Si vous souhaitez améliorer la plateforme, veuillez :

Fork le dépôt.

Créer une nouvelle branche (git checkout -b feature/nouvelle-fonctionnalite).

Effectuer vos modifications.

Committer vos changements (git commit -am 'Ajout d'une nouvelle fonctionnalité').

Pousser vers la branche (git push origin feature/nouvelle-fonctionnalite).

Ouvrir une Pull Request.

# 8. Licence
Ce projet est sous licence MIT. Voir le fichier LICENSE pour plus de détails.

ProX/
├── assets/
│   ├── css/
│   ├── js/
│   └── images/
├── controllers/
│   ├── DemandesEmplois/
│   └── OffresEmplois/
├── includes/
│   ├── DemandesEmplois/
│   ├── OffresEmplois/
│   └── config/
├── models/
│   ├── DemandesEmplois/
│   └── OffresEmplois/
├── sql/
├── views/
│   ├── DemandesEmplois/
│   ├── OffresEmplois/
│   ├── auth/
│   └── partials/
└── fichiers racine

