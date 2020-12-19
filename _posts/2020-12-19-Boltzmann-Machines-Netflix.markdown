---
layout: post
title: "Boltzmann Machines - Netflix"
date: 2020-11-22 21:30:00 +0200
description: "Boltzmann, Machine Learning, Movies"
tags: [Machine Learning,Python,Model,Boltzmann,Netflix,Pandas,pattern,Torch,data]
comments: true
sharing: true
published: true
img: netflixstreaming-2.jpg
---


Dans le cadre de ce projet, nous allons nous lancer dans la création d'une machine de Boltzmann afin de créer un système de recommendation des contenus que l'on peut retrouver sur Netflix.

Pour cela, nous allons commencé par importer les librairies nécessaires.

**Importing** the libraries

```python
import numpy as np
import pandas as pd
import torch
import torch.nn as nn
import torch.nn.parallel
import torch.optim as optim
import torch.utils.data
from torch.autograd import Variable
```

Par la suite, nous allons lire le datasets contenant les contenus provenant de Netflix.

```python
df = pd.read_csv("netflix_titles.csv",sep=",")
df.head()
```
![Screenshot](assets/img/post2_2.PNG/post2_2.png)

# Final thoughts

[The demo project](https://github.com/nalexn/clean-architecture-swiftui) now has **97% test coverage**, all thanks to the Clean Architecture's "dependency rule" and segregation of the app on multiple layers.