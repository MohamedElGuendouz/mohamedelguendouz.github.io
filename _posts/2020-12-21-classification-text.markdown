---
layout: post
title: "Classification de texte - Notes de frais"
date: 2020-11-22 21:30:00 +0200
description: "Classification, NLTK, Machine Learning, Comptability"
tags: [Machine Learning,Python,Model,NLTK,Netflix,Pandas,pattern,Torch,data]
comments: true
sharing: true
published: true
img: supervised-classification.png
---


Dans le cadre de ce projet, nous allons nous essayer de résoudre une problématique lié à la la classification de fichier. 

## Étude de cas : Gestion des notes de frais

Un comptable demande des notes de frais à une entité de son entreprise. Cette entité est composée de plusieurs groupes d'équipes. Chaque groupe est spécifique à un domaine de l'entreprise. 

![](../assets/img/comptable.jpg)

Tous les documents reçus par le comptable son téléchargés mais par manque de temps, sans être classifiées. A la fin du mois de Mars, l'ensemble des groupes de l’entreprise est conviées à un événement annuel sur l'intelligence artificielle à la charge de l'entreprise. 

Au début du mois d'Avril, le comptable souhaite récupérer l'ensemble de notes de frais liés à cette événement. 

![](../assets/img/visuek-ai-france-summit.jpg)

Les notes de frais sont censé contenir un ensemble d'information nous permettant de relié cette note de frais à l'événement. En effet, un certains nombre de réglé de codification ont été définie afin de nommé chaque note de frais.

Le problème ces règles, le comptable s'est rendu compte que le nommage de ces fichiers variés suivant chaque collaborateurs.

En effet, certains ajouté des tirets (-/_) pour séparer les mots. Certains utilisés des abréviations comme FR pour FRANCE ou IA pour machine Learning.

C'est pourquoi le comptable ne s'en sortait plus avec les note de frais.   
  
Désemparait, il alla voir un de ces amis Mohamed (ML Engineer) en lui demandant de l'aidé à trouver une solution à son problème.

Il lui à proposé de réaliser un processus de classification de l'ensemble de ces notes de frais à l'aide d’algorithmes de Machine Learning.

Mohamed brandi sont ordinateur et commença la production des algorithmes de classification.

Il commença par stocker tous les fichiers dans un répertoire qu'il va appelé *notes_de_frais*. Ensuite, il va récupérer tous les noms des fichiers.

## Récupérer les noms des fichiers

```python
import pandas as pd
import glob

repertoire = "notes_de_frais/"
files = glob.glob(repositorie+'*.csv')
list_filename = []
df = None

for i, f in enumerate (files):
    list_filename.append(f[len(repositorie):])

df = pd.DataFrame(list_filename)
```

# Final thoughts

[The demo project](https://github.com/nalexn/clean-architecture-swiftui) now has **97% test coverage**, all thanks to the Clean Architecture's "dependency rule" and segregation of the app on multiple layers.