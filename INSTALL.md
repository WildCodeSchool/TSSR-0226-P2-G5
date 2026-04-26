# Sommaire

1. [Présentation du manuel](#1-présentation-du-manuel) 
2. [Prérequis techniques](#2-prérequis-techniques)
3. [Configuration et Installation sur le serveur Debian](#3-configuration-et-installation-sur-le-serveur-debian)
  - 3.1. [Configuration de IP fixe](#31-configuration-de-ip-fixe)
  - 3.2. [mise à jour du système ](#32-mise-à-jour-du-système)
  - 3.3. [Installation de OpenSSH-Serveur](#33-installation-de-openssh-serveur)
  - 3.4. [Vérification du service](#34-vérification-du-service)
    
4. [Configuration et Installation sur le client Ubuntu](#4-configuration-et-installation-sur-le-client-ubuntu)

  - 4.1. [Mise à jour du système ](#41-mise-à-jour-du-système)
  - 4.2. [Configuration de IP fixe](#42-configuration-de-ip-fixe)
  - 4.3. [Installation de OpenSSH client](#43-installation-de-openssh)
  - 4.4. [Vérification du service](#44-vérification-du-service)
    
5. [Authentification SSH](#5-authentification-ssh)
  - 5.1. [Génération de la clé SSH](#51-Génération-de-la-clé-ssh)
  - 5.2. [Copie de la clé SSH sur le serveur](#52-copie-de-la-clé-ssh-sur-le-serveur)
  - 5.3. [Test de la connexion](#53-test-de-la-connexion)

6. [Déploiement du script](#6-déploiement-du-script)
  - 6.1. [Copier le Script sur le serveur](#61-copier-le-script-sur-le-serveur)
  - 6.2. [Octroie des Permissions](#62-octroie-des-permissions)
  - 6.3. [Exécution du script](#63-exécution-du-script)


## 1. Présentation du manuel
   
   Ce document décrit les étapes nécessaires pour installer et utiliser l’outil d’administration système développé en Bash dans le cadre du projet Scripting en TSSR.
   
   L’environnement repose sur :
    • 1 serveur sous Debian
    • 1 machine cliente sous Ubuntu
    • Une communication sécurisée via SSH
   
## 2. Prérequis techniques

   Les prérequis majeurs pour mener à bien ce travail reposent sur 3 piliers:
   
  **A. Les Machines**

  - Avoir VirtualsBox déjà installé sur sa machine physique
  - Avoir les images ISO à sa disposition pour la création des Vms
  - Vm Serveur => Debian
  - Vm Client => Ubuntu 
      
  **B. Les droits d'Accès**
  
  - Droits administrateurs (sudo) sur les deux machines avant de pouvoir exécuter le script

  **C. Le Réseau**
  
  - Les machines doivent être sur le même réseau
  - La connexion IP fonctionnelle (ping)
  - Vérification des adresses IP sur chaque machines avec la commande :  *ip a*
  - Test de connectivité
    - Depuis **Le client Ubuntu** : ping <Ip_du_Serveur>
    - Depuis le serveur : ping <Ip_du_client>
    
  
 ## 3. Configurations et Installation sur le serveur Debian

  - 3.1. Configuration de IP fixe
       
    -  Identification de la carte réseau et vérification de son activation avec la commande :
        - **ip a**
    
    -  Modification du fichier de configuration réseau avec la commande:
        - **sudo nano /etc/network/interfaces**
        - modifier le fichier en ajoutant des nouveaux paramètres de l'interface réseau *enp0s8* tout en les commentant (#Address secondary) par exemple.

    <img width="883" height="367" alt="Configuration_IP_fixe_serveur" src="https://github.com/user-attachments/assets/34fd8365-dda7-47a2-9f60-4aee0c98f3fd" />
  
    - Après différentes modifications, Redémarrer le service réseau avec la commande:
      
        - **sudo systemctl restart networking**
          
    - Verifier à nouveau que les cartes réseaux serveur et client ont le statut **Up** donc **activé** toujours avec la commande:
        - **ip a**
          
       <img width="841" height="400" alt="Verfication_Carte_Réseau" src="https://github.com/user-attachments/assets/381d2124-9b2f-44d4-bb99-03f4ba98a8f9" />

  - 3.2. Mise à jour du système
    
    - Se connecter avec le compte utilisateur wilder ou en mode root, puis mettre à jour et installer avec la commande suivante:
        - **sudo apt update** : pour mettre à jour les paquets du système
          
<img width="847" height="150" alt="Mise-à-jour_ServeurOpenSSH" src="https://github.com/user-attachments/assets/7945c8fe-ce12-4392-b9f7-06f80720cf01" />
 
  - 3.3. Installation de OpenSSH-Serveur
    
    - **sudo apt install openssh-server -y** : pour installer le serveur OpenSSh
    - **sudo apt update && sudo apt install --only-upgrade openssh-server** : pour mettre à jour uniquement OpenSSH sans toucher au reste des applications.

    <img width="1133" height="366" alt="Installation_ServeurOpenSSH" src="https://github.com/user-attachments/assets/9ee369e4-86a3-4309-b4dc-18be786270d8" />

  - 3.4. Vérification du service
    
    Redémarrer le système avec la commande :
    
      - **systemctl restart ssh** : Pour redémarrer le service ssh dans le système
        
      - **systemctl status ssh** : Pour verifier l'état du ssh dans le système, il doit etre *enabled*
        
        <img width="752" height="308" alt="Statut_du_Service_SSH" src="https://github.com/user-attachments/assets/2af6cfc1-1cf2-47f3-a824-cbbb8b617aac" />
              
## 4. Configurations et Installation sur le client Ubuntu
   
  - 4.1. Mise à jour du système
    
    - Se connecter avec le compte utilisateur wilder ou en mode root, puis mettre à jour avec la commande suivante:
      
        - **sudo apt update** : pour mettre à jour les paquets du système
      
    <img width="977" height="245" alt="Mise_à_jour_Systeme_Client" src="https://github.com/user-attachments/assets/74d11294-f52d-4fe3-9e11-257788eb5435" />
    
  - 4.2. Configuration de IP fixe
    
      - Sur Ubuntu, la configuration de l'IP fixe peut se faire via l'interface graphique.
      - Aller dans *connexions filaires*,puis *Paramètre filaire*. 
      - Cliquer sur la roue cranté pour sélectionner une carte réseau soit la carte *Ethernet enps03* soit la carte *Ethernet enps08*
        <img width="710" height="288" alt="Choix_Carte_Réseau" src="https://github.com/user-attachments/assets/e6cc7132-24a4-4ad3-be59-ca6092d170a7" />

      - Dans l'onglet IPv4,passer du mode de *Automatique* (DHCP) en *mode Manuel* et :
      - Renseigner les champs suivants : *Adresses* , *Masque de réseau* et *DNS*
      - et appuyer sur *appliquer*
        <img width="743" height="478" alt="Activation_Adresse_Fixe_client" src="https://github.com/user-attachments/assets/5e677a2e-1d2c-4d2f-9b23-97330127e528" />
 
  - 4.3. Installation de OpenSSH client

    La procedure ou les étapes d'installation sont presque les mêmes que dans les deux cas(Serveur et Client)
    
    - *sudo apt install openssh -y* : pour installer le service OpenSSh-client
    - *sudo apt update && sudo apt install --only-upgrade openssh* : pour mettre à jour uniquement OpenSSH sans toucher au reste des applications.
      
    <img width="1202" height="327" alt="Installation_OpenSSH_Client" src="https://github.com/user-attachments/assets/e6e6840a-8c0a-453e-b747-fdba3581fd45" />

    
  - 4.4. Vérification du service
    
    Après installation de l'application OpenSSH-client et serveur, activer le service SSH avec les commandes suivantes:
    
      - *sudo systemctl start ssh*
      - *sudo systemctl enable ssh*
        
      <img width="1107" height="135" alt="Vérification_Service_SSH_CLI" src="https://github.com/user-attachments/assets/6e221d4a-b53e-43ff-b9f0-0a838aec635a" />

        
## 5. Authentification SSH

  - 5.1. Génération de la clé SSH
    
    La clé SSH : Est une chaîne de caractères extrêmement longue et complexe générée aléatoirement. Pour "deviner" une clé RSA de 4096 bits, il faudrait des           millénaires avec la puissance de calcul actuelle. D'où, l'importance d'utiliser une clé ssh plutot qu'un mot de passe.
    
    Depuis le *client Ubuntu*, générer une clé ssh avec la commande :
    
    *ssh-keygen* et appuyez sur la touche entrée pour les valeurs par défauts 
    
    <img width="992" height="333" alt="Generercle_ssh" src="https://github.com/user-attachments/assets/a49c8c2b-2a3f-4f85-8f9e-41128c17b291" />

  - 5.2. Copie de la clé SSH sur le Serveur
    
    La commande : *ssh-copy-id <utilisateur>@<addressIPserverssh>* ,elle va chercher la clé publique (généralement située dans: ~/.ssh/id_rsa.pub) sur la machine      locale et l'envoie vers le serveur distant (172.16.50.10) pour l'utilisateur wilder.
    
    <img width="944" height="229" alt="copiecle_vers_Ubuntu" src="https://github.com/user-attachments/assets/8fbe75f9-39e1-477e-b6d9-28da3e5f2330" />
    
  - 5.3. Test de la connexion
    
    Le teste de la connexion se fait à l'aide de la commande: *ssh <utilisateur>@<IP_du_serveur>**

    comme ceci: *ssh wilder@172.16.50.30*

    <img width="687" height="267" alt="Test_de_connexion_depuis_serveur" src="https://github.com/user-attachments/assets/af610879-6e69-4f1d-b85c-4388092a94fa" />

 ## 6. Déploiement du script
    
  - 6.1. Copier le Script sur le serveur

   La commande suivante permet de copier le script depuis la machine cliente(Ubuntu) sur le serveur(debian):
   
   *scp nom_du_fichier.sh <utilisateur>@IP_SERVEUR:/home/utilisateur/*
  
  Par exemple: scp scripting_project.sh wilder@172.16.50.10:/home/wilder/
    
  - 6.2. Octroie des Permissions
    
    - Sur le Serveur:
      
      -  **chmod +x <nom_du_fichier.sh>**
     
  - 6.3. Exécution du script

    - Depuis le serveur, pour exécuter le script, il faut appliquer : **sudo ./<Nom_du_fichier>.sh** ou **sudo bash <Nom_du_fichier>.sh**

  










