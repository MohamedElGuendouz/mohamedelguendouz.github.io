---
layout: post
title: "Use Case : To Big To Fail Company"
date: 2021-04-28 12:00:00 +0200
description: "Notebook Jupyter, Python, NLTK"
tags: [Notebook Jupyter, Python, NLTK]
comments: true
sharing: true
published: true
img: content-kpi.png
---
Dans le cadre de ce projet, nous allons nous lancer dans la création de visualisation, de KPI et de modèles prédictives en partant de données fictives représentant les salariés d'un groupe international.

Pour cela, nous allons commencé par créer les données fictives en utilisant le site Mockaroo.

## Création du datasets

![](../assets/img/Create%20KPI's/Create%20datasets.PNG)


Par la suite, nous allons créer un environnement de travaille sur JupyterLab :

![](../assets/img/Create%20KPI's/Create_environment_in_JupyterLab.PNG)

> Nous allons créer un notebook avec Python 3.

![](../assets/img/Create%20KPI's/creation_of_notebook.PNG)

------------------------------------------------------------------------------------------------------------------

## Importation des données

Une fois avoir défini notre environnement de travail, il nous faut importer les données :

![](../assets/img/Create%20KPI's/import_mock_data.PNG)

## Structure des données

![](../assets/img/Create%20KPI's/get_info_datasets.PNG)

------------------------------------------------------------------------------------------------------------------

## Indicateur de genre dans l'entreprise

Notre première indicateur sera de définir un indicateur permettant de visualiser la répartition des genre au sein du Groupe.  
Pour cela, nous allons utiliser dans un premier temps, la fonction ``` describe() ``` fourni par Pandas.

![](../assets/img/Create%20KPI's/KPI_Genders.PNG)


Puis, nous allons génerer le KPI_Genders permettant de visualiser la proportion comme ceci :

![](../assets/img/Create%20KPI's/KPI_Gender_2.PNG)


Ensuite nous allons calculé l'écart salariale (Wage Gap)

## Wage Gap

Voici un apercu de la formule permettant de créer un ratio exprimant l'écart salariale au sein du groupe :

![](../assets/img/Create%20KPI's/KPI_Wage_Gap.PNG)


------------------------------------------------------------------------------------------------------------------

Maintenant que nous avons notre premier KPI, nous alloons étudié un peu plus nos données.  
  
## Proportion of jobs by salaries

Voici une visualisation des métiers les plus recrutés dans le groupe :
![](../assets/img/Create%20KPI's/proportion_job_by_salaries.PNG)


![](../assets/img/Create%20KPI's/proportion_job_by_salaries_pie.PNG)


> Conclusion : On constate une grande disparité dans les métiers de ce groupe. Mais quant est-il de la disparité des salaires par rapport aux métiers que l'on retrouve dans l'entreprise ?

## Moyenne salariale par métier

![](../assets/img/Create%20KPI's/job_by_salaries.PNG)
