---
layout: post
title: "Create KPI's about salaries"
date: 2021-04-28 12:00:00 +0200
description: "Notebook Jupyter, Python, NLTK"
tags: [Notebook Jupyter, Python, NLTK]
comments: true
sharing: true
published: true
img: content-kpi.png
---
Dans le cadre de ce projet, nous allons nous lancer dans la création de KPI en partant de données fictives représentant les salariés d'une entreprise.

Pour cela, nous allons commencé par créer les données fictives en utilisant le site Mockaroo.

## Création du datasets

![](../assets/img/Create%20KPI's/Create%20datasets.PNG)

Par la suite, nous allons créer un environnement de travaille sur JupyterLab :

![](../assets/img/Create%20KPI's/Create_environment_in_JupyterLab.PNG)

> Nous allons créer un notebook avec Python 3.

![](../assets/img/Create%20KPI's/creation_of_notebook.PNG)

## Importation des données

Une fois avoir défini notre environnement de travail, il nous faut importer les données :

![](../assets/img/Create%20KPI's/import_mock_data.PNG)


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

Lancer Visual Studio Code.

Pour créer une application Angular 9, il nous faut installer Angular CLI.

```
npm install -g @angular/cli@9.0.2
```

Par la suite, nous allons créer l'application que l'on va nommer frontend comme ceci :

```
ng new frontend --routing --style css
```

Une fois le projet généré, lancé l'application.

```
ng serve --open
```

L'application sera accessible a cette URL :  
```
http://localhost:4200
```
