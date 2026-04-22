1. [Présentation du pseudo-code](#1-présentation_du_pseudo-code) 
2. [Prérequis](#2-prérequis)
3. [Lancement du script](#3-lancement_du_script)
4. [Présentation interface du script](#4-présentation_interface_du_script)
  - 4.1 [Gestion Machine](#41-gestion_machine)
  - 4.2. [Gestion Répertoires ](#42-gestion_répertoires)
  - 4.3. [Gestion Utilisateurs](#43-gestion_utilisateurs)
  - 4.4. [Gestion Mot de passe utilisateurs](#44-gestion_mot_de_passe_utilisateurs)
  - 4.5. [Gestion Groupes](#45-gestion_groupes)
  - 4.6. [Informations système](#46-informations_système)
  - 4.7. [Menu Principal](#47-menu_principal)
  - 4.8. [Quitter le script](#48-quitter_le_script)


    

## 1. Présentation du pseudo-code

Le pseudo-code utilisé dans le cadre de ce projet décrit un programme interactif en mode console permettant la gestion d’un système Linux. Il est organisé sous forme de menus hiérarchiques accessibles en boucle. 

Chaque menu fonctionne avec une boucle TANT QUE permettant de revenir au menu précédent.
Les actions sont sélectionnées via des structures conditionnelles (SELON / CAS).
Des vérifications sont faites avant chaque opération (existence utilisateur, dossier, etc.).
Le programme s’arrête uniquement lorsque l’utilisateur choisit "0 - Quitter" dans le menu principal.

## 2. Prérequis

- Avoir tous les matériels bien installés (VMs, SSH et les adresses IP fixes configurés)
- Avoir les deux machines allumées: CLILIN01 et SRVLX01
- Se rassurer que les deux machines communiquent en les pingant 
- Vérifier que le SSH et sa clé sont configurés et actifs sur le client avec *sudo systemctl status ssh*  et sur le serveur avec *sudo systemctl status ssh-server*.
- Faire un test de connexion en root avec le compte utilisateur client ssh wilder@172.16.50.30

## 3. Lancement du script

Le script commence par une vérification des privilèges utilisateur "sudo".

  - Condition initiale
      - Le programme teste si l’utilisateur courant possède les droits administrateur (root).
      - Cette vérification se fait à l’aide de l’identifiant utilisateur (EUID).
 
          - Deux cas possibles :

              - Si l’utilisateur est root :
                Le script continue son exécution et accède ensuite au menu principal.

              - Si l’utilisateur n’est pas root :

                Un message d’avertissement s’affiche :"Ce script ne peut être lancé qu’avec les droits administrateur (sudo)".
                Le script s’arrête immédiatement avec un code d’erreur.
                Cette étape garantit la sécurité et le bon fonctionnement du script.

## 4. Présentation interface du script

  ### - 4.1. Gestion Machine
    
  Permet d’effectuer des actions sur le système : 1.Verrouiller la session en cours et 2.Redémarrer la machine
  
  <img width="482" height="172" alt="Menu_Gestion_Machine" src="https://github.com/user-attachments/assets/6e2b525c-9dbd-4750-9f0c-0a9a233e5454" />
    
  ### - 4.2. Gestion Répertoires
    
  Permet de gérer les dossiers. Il est constitué de deux sous-menus suivants :
    
  - Créer un répertoire (s’il n’existe pas)
  - Supprimer un répertoire (avec confirmation)
   
    <img width="546" height="205" alt="Gestion de répertoire" src="https://github.com/user-attachments/assets/6504dbf3-b2a8-4716-a49e-554b7a1cae4c" />

  ### - 4.3. Gestion Utilisateurs
    
  Permet de gérer les comptes utilisateurs. Il est composé de sous-menus suivants :

  - Créer un utilisateur
  - Supprimer un utilisateur
  - Accéder à la gestion du mot de passe
    
    <img width="487" height="206" alt="Menu_Gestion_Utilisateurs" src="https://github.com/user-attachments/assets/c4216476-4d86-4172-b41b-ac2cbbe754ec" />


  ### - 4.4. Gestion Mot de passe utilisateurs

  Il est spécifique à un utilisateur :

  Il permet de:
    
  - Définir un mot de passe (après création de l'utilisateur)
       
  - Supprimer un mot de passe

    <img width="480" height="181" alt="Gestion_mot_de_passe" src="https://github.com/user-attachments/assets/7809972e-8a89-409a-8ef3-8bf2ff6a221b" />


  ### - 4.5. Gestion Groupes

  Permet de gérer les groupes:

  - Ajouter un utilisateur au groupe administrateur (sudo)
  - Ajouter un utilisateur à un groupe (créé si nécessaire)

    <img width="462" height="187" alt="Gestion_Groupe" src="https://github.com/user-attachments/assets/87566a87-5013-4d2a-9004-d1562fc7bb60" />

  ### - 4.6. Informations système
  
  Ce menu permet d’afficher des informations sur le système notamment :

  - Dernières connexions
  - Version du système d’exploitation
  - Espace disque (partitions)
  - Mémoire RAM
    
    <img width="438" height="212" alt="Informations_du_Système" src="https://github.com/user-attachments/assets/4780a83d-32d5-4ca1-8505-ba84c1a8b8e9" />
    
  ### - 4.7. Menu Principal
    
  Point d’entrée du programme.
    
  Il permet d’accéder aux différentes fonctionnalités de base notamment :

  - Machine
  - Répertoires
  - Utilisateurs
  - Groupes
  - Informations système
  - Quitter le programme

  <img width="726" height="297" alt="Menu_Principal" src="https://github.com/user-attachments/assets/647e47a0-e7de-46ae-b3a4-bdd276bcf94a" />


  ### - 4.8. Quitter le script

  Permet de fermer le programme proprement en séléctionnant zero(0).
