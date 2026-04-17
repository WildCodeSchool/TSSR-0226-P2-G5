# Sommaire

1. [Présentation du manuel](#1-présentation-du-manuel) 
2. [Prérequis techniques](#2-prérequis-techniques)
3. [Installation sur le serveur Debian](#3-installation-sur-le-serveur-debian)
  - 3.1. [Configuration de IP fixe](#31-configuration-de-ip-fixe)
  - 3.2. [mise à jour du système ](#32-mise-à-jour-du-système)
  - 3.3. [Installation de OpenSSH-Serveur](#33-installation-de-openssh-serveur)
  - 3.4. [Vérification du service](#34-vérification-du-service)
    
4. [Installation sur le client Ubuntu](#4-installation-sur-le-client-ubuntu)

  - 4.1. [Mise à jour du système ](#41-mise-à-jour-du-système)
  - 4.2. [Configuration de IP fixe](#42-configuration-de-ip-fixe)
  - 4.3. [Installation de OpenSSH client](#43-installation-de-openssh)
  - 4.4. [Vérification du service](#44-vérification-du-service)
    
5. [Connexion SSH](#5-connexion-ssh)
  - 5.1. [Génération de la clé SSH](#51-Génération-de-la-clé-ssh)
  - 5.2. [Copie de la clé SSH](#52-copie-de-la-clé-ssh)
  - 5.3. [Test de la connexion](#53-test-de-la-connexion)

1. Présentation du manuel
   Ce document décrit les étapes nécessaires pour installer et utiliser l’outil d’administration système développé en Bash dans le cadre du projet Scripting en       TSSR.
   
2. Prérequis techniques
  - Avoir VirtualsBox déjà installé sur sa machine physique
  - Avoir les images ISO à sa disposition pour la création des Vms
  - S'assurer d'avoir toutes les VMs sur le même Réseau dans VirtualBox.
  - Système de distribution Linux : Débian et Ubuntu
  - Avoir droit d'Administrateur sudo avant d'exécuter le script
   
3. Installation sur le serveur Debian

  - 3.1. Configuration de IP fixe
    - Se connecter avec le compte utilisateur wilder ou en mode root, puis mettre à jour et installer avec les commandes suivantes:
        - **sudo apt update** : pour mettre à jour les paquets du système
          
    -  Identification de la carte réseau et vérification de son activation avec la commande :
      
        - **ip a**
    -  Modification du fichier de configuration réseau avec la commande:
      
        - **sudo nano /etc/network/interfaces**

    <img width="883" height="367" alt="Configuration_IP_fixe_serveur" src="https://github.com/user-attachments/assets/34fd8365-dda7-47a2-9f60-4aee0c98f3fd" />
  
    - Après différentes modifications, Redémarrer le service réseau avec la commande:
        - **sudo systemctl restart networking**
    - Verifier que les cartes réseaux serveur et client ont le statut **Up** donc **activé** 

  - 3.2. Mise à jour du système
     
<img width="847" height="150" alt="Mise-à-jour_ServeurOpenSSH" src="https://github.com/user-attachments/assets/7945c8fe-ce12-4392-b9f7-06f80720cf01" />
 
  - 3.3. Installation de OpenSSH-Serveur
    
    - **sudo apt install openssh-server** :pour installer le serveur OpenSSh
    - **sudo apt update && sudo apt install --only-upgrade openssh-server** : pour mettre à jour uniquement OpenSSH sans toucher au reste des applications.

    <img width="1133" height="366" alt="Installation_ServeurOpenSSH" src="https://github.com/user-attachments/assets/9ee369e4-86a3-4309-b4dc-18be786270d8" />

  - 3.4. Vérification du service
    
    Redémarrer le système avec la commande : 
    
4. Installation sur le client Ubuntu
  - 4.1. Mise à jour du système
  - 4.2. Configuration de IP fixe
  - 4.3. Installation de OpenSSH client
  - 4.4. Vérification du service
5. Connexion SSH
  - 5.1. Génération de la clé SSH
  - 5.2. Copie de la clé SSH vers le Client
  - 5.3. Test de la connexion


