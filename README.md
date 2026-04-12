# TSSR-0226-P2-G5

# SOMMAIRE



1. [Présentation du projet](#1-présentation-du-projet)
2. [Contexte du projet](#2-contexte-du-projet)
3. [Technologies utilisées et Choix techniques](#3-technologies-utilisées-et-choix-techniques)
  - 3.1 [Virtualisation](#31-virtualisation)
  - 3.2 [Système explotation](#32-système-exploitation)
  - 3.3 [Langages de script](#33-langages-de-script)
  - 3.4 [Gestion de version](#34-gestion-de-version)
4. [Fonctionnalités des scripts](#4-fonctionnalités-des-scripts)
  - 4.1 [Gestion des machines](#41-gestion-des-machines)
  - 4.2 [Gestion des utilisateurs](#42-gestion-des-utilisateurs)
  - 4.3 [Collecte informations ](#43-collecte-informations)
  - 4.4 [Interface](#44-interface)
  - 4.5 [Option Sortir](#45-option-sortir)
5. [Difficultés rencontrées](#5-difficultés-rencontrées)
6. [Améliorations possibles](#6-améliorations-possibles)



## 1. Présentation du projet

Le projet consiste à concevoir un outil d’administration centralisée multi-plateforme. Cet outil doit permettre à un administrateur d'exécuter des commandes à distance et de collecter des informations sur une machine cliente(Linux-Ubuntu) à partir d'un serveur dédié(Linux-Débian) au sein d'un même réseau.

## 2. Contexte du projet
Le projet s'inscrit dans un cadre d'apprentissage des compétences de Technicien Supérieur Systèmes et Réseaux (TSSR). Il simule un environnement professionnel où l'automatisation des tâches récurrentes est essentielle pour maintenir une infrastructure. L'ensemble des machines (serveur et client) évoluent sur un réseau privé commun (172.16.50.0/24)

## 3. Technologies utilisées et Choix techniques

### 3.1 Virtualisation 
La technologie de virtualisation utilisée est VirtualBox pour héberger les machines virtuelles (VM).
### 3.2 Système exploitation

- Serveur : **Linux** (Débian 13)
- Client : **Linux** (Ubuntu 24) 
### 3.3 Langages de script
Pour l'environnement Linux, le langage utilisé est **Bash**    
### 3.4 Gestion de version
GitHub pour le dépôt de code et des documents.

## 4. Fonctionnalités des scripts
Les scripts doivent proposer une navigation via un menu ergonomique permettant de choisir une cible (client) et une action à mener:
### 4.1 Gestion des machines
- Arrêt et redémarrage
- Execution des commandes à distances
- Interrogation du système (Version OS ou état de machine)
### 4.2 Gestion des utilisateurs
- Création et Suppression
- Modification mot de passe
- Informations (dernière connexion et changement de mot de passe)
### 4.3 Collecte informations
- Système
- Utilisateur
### 4.4 Interface
- Menu interactif
- Choix
    - cible(client)
    - Action ou information
### 4.5 Option Sortir
L'option **Sortir** ou **quitter** permet de quitter le script de manière propre et ergonomique.

## 5. Difficultés rencontrées

  - La gestion de la communication à distance (SSH entre serveur et client).
  - La manipulation et l'analyse du "pseudo-code" pour le transformer en script fonctionnel.
  - Le débogage des scripts lors des phases de tests intensifs.

## 6. Améliorations possibles
