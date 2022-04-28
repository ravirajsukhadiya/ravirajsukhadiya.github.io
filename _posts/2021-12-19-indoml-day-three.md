---
layout: post
title:  IndoML 2021 Day 3 
date:   2021-12-19 00:00:00 
description: Talks at IndoML
---

##### Credits: <a href="https://shruti-singh.github.io/" target="blank">Shruti Singh</a>
## Mohit Bansal: Knowledgeable & Spatial-Temporal Vision+Language
[<img src="https://i.imgur.com/uYHNIEj.png" width="100%"/>]()
[<img src="https://i.imgur.com/fPtuDGI.png" width="100%"/>]()
[<img src="https://i.imgur.com/vs2sJht.png" width="100%"/>]()
[<img src="https://i.imgur.com/j6B0LMS.png" width="100%"/>]()
[<img src="https://i.imgur.com/UNHqJOq.png" width="100%"/>]()
[<img src="https://i.imgur.com/79xY5Se.png" width="100%"/>]()
[<img src="https://i.imgur.com/tRhHSbz.png" width="100%"/>]()


## Robert Hoehndorf: Machine learning with ontologies in biomedicine

[<img src="https://i.imgur.com/qYNynaS.png" width="100%"/>]()
While there are multiple types of datasets, the big challenge is to combine these in a meaningful way so that we can connect how the knowledge from genome, trancsriptome, metabolome etc are related.

Biomedicine is a knowledge-driven dicipline where a lot of information comes from more than 100 years of experiments. This is the reason for large biomedical knowledge bases. If we want to build models in biomedicine, which do anything complex, we also need to consider ontologies. An ontology is an explicit conceptualization of a domain, and in terms of axioms define how concepts are related. Currently, there are over 500 biomedical ontologies.
[<img src="https://i.imgur.com/AYh55WK.png" width="100%"/>]()

[<img src="https://i.imgur.com/y8Yh4Zj.png" width="100%"/>]()

* Embedding Formal Knowledge
An embedding is a map (morphism) from one mathematical structure X into another structure Y:
$f: X \rightarrow Y$, 
such that $X$ is preserved in $Y$.
[<img src="https://i.imgur.com/cO3yVOT.png" width="100%"/>]()

We need some mapping from ontologies to graphs.
[<img src="https://i.imgur.com/rOYdJKL.png" width="100%"/>]()

Once we have a graph from the ontology, then we can also get graph embedding using various algorithms such as Node2Vec or RandomWalk, TransE, or Word2Vec.

[<img src="https://i.imgur.com/WPsspmU.png" width="100%"/>]()

We started with a simple problem of relation prediction in a graph. Remove some edges, and then try to predict them via some ML algo. 
[<img src="https://i.imgur.com/brDHK0D.png" width="100%"/>]()
The results obtained via with or without reasoning didn't vary much, which was frutrating. It was expected that if we are able to use the axioms in the ontologies, then the graph in the KG well enough, then the performance should increase substantially. However, the axioms are hard to represent in a graph (see examle below).
[<img src="https://i.imgur.com/VixWAzt.png" width="100%"/>]()

So the question is, is there a way to embed these axioms? Some ideas such as Onto2Vec apply a LM to the axioms directly. But then there is no way to use the priori semantics that we know the axioms follow. For example, sigma-algebra structures such as top-concept, bottom-concept, singleton sets, etc which are used in first-order logic to define syntax and semantics between concepts and relations.
[<img src="https://i.imgur.com/qbPwome.png" width="100%"/>]()


We want to find an embedding that generates a model of the axioms in the ontology. The model means that the axioms in the ontology are true in the model.

We define an embedding for relations and classes. We map our classes to n-balls, such that points which are within the sphere/ball will be in extension of the concept. Each concept is mapped to n-ball, and we map relations as transformations between them.

Discuion of A-boxes and other ontology specific things. Summmary slide:
[<img src="https://i.imgur.com/B0h7rJ3.png" width="100%"/>]()


## Marinka Zitnik: Infusing Structure and Knowledge Into Biomedical AI

[<img src="https://i.imgur.com/0d2A2ft.png" width="100%"/>]()
We need to integrate humungou amounts of diverse datasets which is challenging. In terms of building ML models, accuracy alone is not enough. Explanations, and fairness are important. 

[<img src="https://i.imgur.com/YNee59a.png" width="100%"/>]()
[<img src="https://i.imgur.com/RIlbzbp.png" width="100%"/>]()
[<img src="https://i.imgur.com/IhyQ1Mk.png" width="100%"/>]()


1. Infusing structure into Biomedical AI
Few Shot Learning on Graphs
Existing GNNs require abundant labels, which are scarce in non CS datasets. Such as developing drugs, novel emerging diseases etc.

[<img src="https://i.imgur.com/T6GNFYn.png" width="100%"/>]()
The assumption that the graph is richly labelled(indicated by node color) and hence a GNN clasifier can be trained accurately, is wrong. Most nodes are unknown or have little knowledge as is seen in the right graph. Few-shot learning is essential in such scenarios.

**Few-Shot learning:** Only few example per label are present.
[<img src="https://i.imgur.com/29MUKYl.png" width="100%"/>]()
2-shot, 3-way: 2 classes for prediction, and for each class, we have only 2 labelledexamples/shots. The two stages are:
    i. Meta-Training: Take a model and  train it in such a way that we ask it to solve a large number of training tasks where each task is designed to be very challenging. As the model learns new tasks, it will become better and better at quickly leaning/adapting to other tasks. We want to identify a mechanism to transfer information from one training task to another so that eventually it becomes better at adaption to new tasks as it has already seen so many tasks.
    ii. Meta-Test: 
    
Few-Shot for Graphs:
One algo is G-Meta (NeurIPS)
[<img src="https://i.imgur.com/uQ78sKM.png" width="100%"/>]()
Training phase: learn different labels (represented by different shades of yellow). Train task 1 has a process to learn a better initialization for training task 2. This is then repeated for training task 3 and so on.
[<img src="https://i.imgur.com/NiDrvKA.png" width="100%"/>]()

The key idea behind quick adaption to learn new tasks is the notion of local subgraphs. In addition to learning d-dim node embeddings, we alo learn subgraph signature functions. That signatures represents the task in a very effective manner. The signature function is defined by looking at local neighbouring subgraphs around nodes that are labelled for that task.
[<img src="https://i.imgur.com/vvtWxsb.png" width="100%"/>]()

Now, why use local subgraphs for signature function? (Read TL;DR)
[<img src="https://i.imgur.com/0tBl4Pd.png" width="100%"/>]()
[<img src="https://i.imgur.com/KGJaV9A.png" width="100%"/>]()

***Next: Application in biomedical dicovery***
Rapid Therapeutic Innovation
[<img src="https://i.imgur.com/GWa2RHT.png" width="100%"/>]()
[<img src="https://i.imgur.com/lbJruCz.png" width="100%"/>]()
[<img src="https://i.imgur.com/TFsS58D.png" width="100%"/>]()


Each training task was defined for a different disease. GMeta had to predict which drugs will work or not work for that disease (approved vs unapproved drugs). The earlier training tasks were for known diseases for which some treatments were available.
[<img src="https://i.imgur.com/EUUHnV5.png" width="100%"/>]()


GMeta outperformed other network difussion based algos and classic drug repurposing algos.
[<img src="https://i.imgur.com/myAI4P9.png" width="100%"/>]()