---
layout: post
title:  IndoML 2021 Day 1 
date:   2021-12-17 00:00:00 
description: Talks at IndoML
---

##### Credits: <a href="https://shruti-singh.github.io/" target="blank">Shruti Singh</a>
## Sameer Singh: Evaluating and Testing Natural Language Processing Models

How do you define if a new model X is better than an old model Y? One way is to pick a task such as QnA, and compare the accuray of both of these models. This is generally recorded by leaderboards, such as SQuAD. Instead, some one said it is better to compare on a bunch of tasks, one example being GLUE and Super-GLUE. However, there are a lot of issues in these models depite their high acuracies there are multiple issues. Some are:
* Shortcuts (right for wrong reasons)
* Sensitive to phrasing
* Sensitive to typos

Problems with leaderboards:
* Duplicate the bias of data collection
* Single metric is insufficinet
* Model capabilities are unknown

The truth is that we don't really know how to compare two models, or effectively evaluate which model is better for what reasons?


* Perturbation-based Testing
 (X, y) -> Transformation -> (X', y') -> Model -> $y^{\^}$
 These could be automatic or manual. 
 ***Automatic***: SEAR (ACL 2018), Triggers (EMNLP 2019), CRIAGE (NAACL 2019)
 ***Manual***: Implications (ACL 2019), Contrast Sets (FEMNLP 2020)
 A Testing Framework: Checklist (ACL 2020)

Universal Adversarial Triggers: Short phrases when added as a prefix to any input, will drop the model accuracy drastically. Models such as sentiment (or classifiers), or QA models. For example, we we can add a phrase "why how because to kill american people" when added to the paragraph, 2/3 of the answers to questions pick the answer "to kill american people".
SEARS: Paraphraical edits (which keep the meaning same). Characterizing via rules. Change the question so that the answer is inconsistent.

<hr>

## Tim Baldwin: Fairness in Natural Language Processing
Some examples of Unfair AI:
* Twitter's auto-cropping algo: cchooses people with specific features, from specific racial bakgrounds etc.
* Bias in US mortgrage approvals.
* NLP technologies, such as languge identification libraries

Particular protected attributes of interest (gender, race, age, etc) vary greatly across datasets, based on data availabilty, task, and specific interest of researchers.

Talk Outline:
**1. Baseline Approaches for Mitigating Bias**
**2. Mitigating Bias with Adversarial Learning and Beyond**

* **Training Models to be Fair(er)**
It in't enough to not include the protected attributes. Sometimes, naively trained models pick up and amplify bias. If the cause is imbalance in terms of protected attributes, then prebalancing may help (Wang et al 2019). 
Another way could be to train a model to be as good as possible at predicting the target and as bad as possible to predict the hidden attributes, via adversarial learning.
One "Adversarial discriminator" per protected attribute, which predict the values of these attributes via the hidden representations. Train via min-max, i.e. minimize the cross entropy over target and maximize the CE over the protected variable. Use an iterative apporoach, where fix the discriminator and minimize the CE for target, then fix the parameters for the model, and then train the adversarial dicriminator.
E.g.: POSTagging - biLSTM model and a single FFlayer applied to final hidden representation used as an adversarial discriminator. Protected attrs were age and gender. Evaluate accuracy for both in-domain and cross-domain setting.

* **Issue 1: Training Instability**
Could be difficult to train (failure to converge). Difficult for complex models/tasks. Some engineering solutions are: add extra capacity to the adversarial discriminators, upweight teh adversarial loss term(s), ensemble the discriminator. One issue with naive ensembling of dicriminators is tha there is no constraint that they complement each other, so one fix is to introduce a orthogonality constraint on the parameters of the adversarie in a given ensemble (Bousmalis et al 2016).  This enforces diversity in adversarial discriminator.
Findings: 
    * Ensemble of discriminators > single discriminator > vanilla model. 
    * Better and more stable results with orthogonality constraints on ensemble

* **Issue 2: Unavailibilty of protected attributes for some users**
 The training of the adv dicriminator is decoupled from the base model, so we can just train the discriminator onthe subset of attributes that are present. Also possible to transfer the protected attributes between tasks/datasets with diffrerent target varibale from external domains.
 [<img src="https://i.imgur.com/h4tVgoG.png" width="100%"/>]()

* **Intersectional Bias**
 The orthogonality onstraint enhanes the per-attribute performance, but it might not be good at capturing the interaction between protected attributes. So instead of looking at these attributes as independent groups, we can create Intersectional Groups (non overlapping, exhautive combinations, of groups), or Gerrymandering Interetional Groups (overlapping ubgroups defined by iterection fo any subset of private attributes). 
[<img src="https://i.imgur.com/zDThQ43.png" width="100%"/>]()
[<img src="https://i.imgur.com/kDyqS4N.png" width="100%"/>]()
[<img src="https://i.imgur.com/9ntl2AB.png" width="100%"/>]()

<!--
Jean shorts raw denim Vice normcore, art party High Life PBR skateboard stumptown vinyl kitsch. Four loko meh 8-bit, tousled banh mi tilde forage Schlitz dreamcatcher twee 3 wolf moon. Chambray asymmetrical paleo salvia, sartorial umami four loko master cleanse drinking vinegar brunch. <a href="https://www.pinterest.com" target="blank">Pinterest</a> DIY authentic Schlitz, hoodie Intelligentsia butcher trust fund brunch shabby chic Kickstarter forage flexitarian. Direct trade <a href="https://en.wikipedia.org/wiki/Cold-pressed_juice" target="blank">cold-pressed</a> meggings stumptown plaid, pop-up taxidermy. Hoodie XOXO fingerstache scenester Echo Park. Plaid ugh Wes Anderson, freegan pug selvage fanny pack leggings pickled food truck DIY irony Banksy.

#### Hipster list
<ul>
    <li>brunch</li>
    <li>fixie</li>
    <li>raybans</li>
    <li>messenger bag</li>
</ul>

Hoodie Thundercats retro, tote bag 8-bit Godard craft beer gastropub. Truffaut Tumblr taxidermy, raw denim Kickstarter sartorial dreamcatcher. Quinoa chambray slow-carb salvia readymade, bicycle rights 90's yr typewriter selfies letterpress cardigan vegan.

<hr>

Pug heirloom High Life vinyl swag, single-origin coffee four dollar toast taxidermy reprehenderit fap distillery master cleanse locavore. Est anim sapiente leggings Brooklyn ea. Thundercats locavore excepteur veniam eiusmod. Raw denim Truffaut Schlitz, migas sapiente Portland VHS twee Bushwick Marfa typewriter retro id keytar.

<blockquote>
    We do not grow absolutely, chronologically. We grow sometimes in one dimension, and not in another, unevenly. We grow partially. We are relative. We are mature in one realm, childish in another.
    —Anais Nin
</blockquote>

Fap aliqua qui, scenester pug Echo Park polaroid irony shabby chic ex cardigan church-key Odd Future accusamus. Blog stumptown sartorial squid, gastropub duis aesthetic Truffaut vero. Pinterest tilde twee, odio mumblecore jean shorts lumbersexual.
-->