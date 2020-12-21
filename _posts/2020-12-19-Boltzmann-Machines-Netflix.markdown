---
layout: post
title: "Boltzmann Machines - Netflix"
date: 2020-11-22 21:30:00 +0200
description: "Boltzmann, Machine Learning, Movies"
tags: [Prediction]
comments: true
sharing: true
published: true
img: netflixstreaming-2.jpg
---


Dans le cadre de ce projet, nous allons nous lancer dans la création d'une machine de Boltzmann afin de créer un système de recommendation des contenus que l'on peut retrouver sur Netflix.

Pour cela, nous allons commencé par importer les librairies nécessaires.

## Importer les librairies

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
## Lire les données
Par la suite, nous allons lire le Datasets contenant les contenus provenant de Netflix.

```python
df = pd.read_csv("netflix_titles.csv",sep=",")
df.head()
```
![](../assets/img/post2_2.PNG)


Par la suite, on converti le Dataset en deux dictionnaires training_set et test_set

## Obtenir le nombre d'utilisateurs et de films
```python
nb_users = int(max(max(training_set[:,0]), max(test_set[:,0])))
nb_movies = int(max(max(training_set[:,1]), max(test_set[:,1])))
```
## Convertir les données en un tableau avec les utilisateurs en lignes et les films en colonnes

```python
def convert(data):
    new_data = []
    for id_users in range(1, nb_users + 1):
        id_movies = data[:,1][data[:,0] == id_users]
        id_ratings = data[:,2][data[:,0] == id_users]
        ratings = np.zeros(nb_movies)
        ratings[id_movies - 1] = id_ratings
        new_data.append(list(ratings))
    return new_data
training_set = convert(training_set)
test_set = convert(test_set)
```

## Conversion des données en *Torch tensors*
```python
training_set = torch.FloatTensor(training_set)
test_set = torch.FloatTensor(test_set)
```

## Conversion des notes en notes binaires 1 (aimé) ou 0 (non aimé)

```python
training_set[training_set == 0] = -1
training_set[training_set == 1] = 0
training_set[training_set == 2] = 0
training_set[training_set >= 3] = 1
test_set[test_set == 0] = -1
test_set[test_set == 1] = 0
test_set[test_set == 2] = 0
test_set[test_set >= 3] = 1
```

## Création de l'architecture du réseau de neurones

```python
class RBM():
    def __init__(self, nv, nh):
        self.W = torch.randn(nh, nv)
        self.a = torch.randn(1, nh)
        self.b = torch.randn(1, nv)
    def sample_h(self, x):
        wx = torch.mm(x, self.W.t())
        activation = wx + self.a.expand_as(wx)
        p_h_given_v = torch.sigmoid(activation)
        return p_h_given_v, torch.bernoulli(p_h_given_v)
    def sample_v(self, y):
        wy = torch.mm(y, self.W)
        activation = wy + self.b.expand_as(wy)
        p_v_given_h = torch.sigmoid(activation)
        return p_v_given_h, torch.bernoulli(p_v_given_h)
    def train(self, v0, vk, ph0, phk):
        self.W += (torch.mm(v0.t(), ph0) - torch.mm(vk.t(), phk)).t()
        self.b += torch.sum((v0 - vk), 0)
        self.a += torch.sum((ph0 - phk), 0)
```
```python
nv = len(training_set[0])
nh = 100
batch_size = 100
rbm = RBM(nv, nh)

```
## Entraîner le RBM
```python
nb_epoch = 10
for epoch in range(1, nb_epoch + 1):
    train_loss = 0
    s = 0.
    for id_user in range(0, nb_users - batch_size, batch_size):
        vk = training_set[id_user:id_user+batch_size]
        v0 = training_set[id_user:id_user+batch_size]
        ph0,_ = rbm.sample_h(v0)
        for k in range(10):
            _,hk = rbm.sample_h(vk)
            _,vk = rbm.sample_v(hk)
            vk[v0<0] = v0[v0<0]
        phk,_ = rbm.sample_h(vk)
        rbm.train(v0, vk, ph0, phk)
        train_loss += torch.mean(torch.abs(v0[v0>=0] - vk[v0>=0]))
        s += 1.
    print('epoch: '+str(epoch)+' loss: '+str(train_loss/s))
```

## Tester le RBM
```python
test_loss = 0
s = 0.
for id_user in range(nb_users):
    v = training_set[id_user:id_user+1]
    vt = test_set[id_user:id_user+1]
    if len(vt[vt>=0]) > 0:
        _,h = rbm.sample_h(v)
        _,v = rbm.sample_v(h)
        test_loss += torch.mean(torch.abs(vt[vt>=0] - v[vt>=0]))
        s += 1.
print('test loss: '+str(test_loss/s))
```


# Final thoughts

[The demo project](https://github.com/nalexn/clean-architecture-swiftui) now has **97% test coverage**, all thanks to the Clean Architecture's "dependency rule" and segregation of the app on multiple layers.