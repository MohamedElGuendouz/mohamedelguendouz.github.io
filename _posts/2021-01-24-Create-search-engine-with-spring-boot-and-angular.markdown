---
layout: post
title: "Create Search Engine with Spring-boot & Angular"
date: 2021-01-24 15:38:00 +0200
description: "Spring boot, Angular, Search Engine"
tags: [Spring boot, Angular, Search Engine]
comments: true
sharing: true
published: true
img: netflixstreaming-2.jpg
---
Dans le cadre de ce projet, nous allons nous lancer dans la création d'un moteur de recherche. Ce moteur de recherche aura pour objectif de nous retourner un ensemble de GIFS associés à un ou plusieurs mot clés.  
  
Pour cela, nous allons utiliser Giphy pour réccupérer les GIFS ainsi que Spring-boot & Angular comme langages de programmation.

Pour cela, nous allons commencé par créer le projet Spring-boot via l'outil IntelliJ IDEA.

## Création du projet Spring Boot

![](../assets/img/search-engine/create%20project%20in%20intelliJ%20IDEA.png)

Nous allons définir le projet comme ceci :

![](../assets/img/search-engine/init%20project.png)


Par la suite, nous allons ajouter ces dépendances :

![](../assets/img/search-engine/add%20dependancies.png)

Une fois avoir choisi l'emplacement du projet, on se retrouve avec un ensemble de fichiers de cette forme :

![](../assets/img/search-engine/arboresence%20spring%20boot.png)


Avec ces dépendances dans le fichier pom.xml :

![](../assets/img/search-engine/list%20dependancies%20spring%20boot.png)

## Générer le projet 

Pour cela, il faut effectuer un clique droit sur le projet et cliquer sur Build le module.

## Lancer le projet 

Ensuite, on lance le projet en faisant un clique droit sur le fichier principal et en cliquant sur Run :

![](../assets/img/search-engine/lancer%20le%20projet%20spring%20boot.png)

Une fois le projet lancé, il devrait apparaitre un terminal avec le résultat du Run.

Pour ceux qui aurait ce type de problème :

![](../assets/img/search-engine/port%208080.png)

C'est que votre port 8080 est déjà utilisé. Il va donc falloir changé le port lors du lancement du projet. 

Pour cela, on ajoute *server.port=9090* dans le fichier *application.properties*

##### On rebuild le projet et on relance le programme.

Vous devrier voir ceci :
![](../assets/img/search-engine/finished%20first%20run.png)

Et ça dans votre navigateur :

![](../assets/img/search-engine/first%20apercu%20in%20navigateur.png)

## Créer le projet Angular 
Arrêter le processus du projet Spring Boot.


Lancer Visual Studio Code.

Créer un projet vide comme ceci :

![](../assets/img/search-engine/create%20project%20angular.png)

Initialisation du projet :

![](../assets/img/search-engine/init%20project%20angular.png)

Vous devriez avoir ce type d’arborescence a la fin de l’initialisation :

![](../assets/img/search-engine/arboresence%20angular.png)


## Création du template avec Bootstrap Studio


![](../assets/img/search-engine/create%20template%201.png)

On défini la page sous cette forme en n’oubliant pas d'ajouter un container dans la section :

![](../assets/img/search-engine/init%20template.png)


On y ajouter un card group :

![](../assets/img/search-engine/card%20group.png)

et suprimer les body de cette forme : 

![](../assets/img/search-engine/hidden%20body.png)

Nous avons fini avec la définition du template. On va passé maintenant à la configuration du projet Spring Boot.