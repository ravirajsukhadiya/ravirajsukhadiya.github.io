---
layout: post
title:  IndoML 2021 Day 2 
date:   2021-12-18 00:00:00 
description: Talks at IndoML
---

##### Credits: <a href="https://shruti-singh.github.io/" target="blank">Shruti Singh</a>
## Ido Dagan: Novel data for modeling textual information: decomposition, multi-text, and interaction

Two types of data in NLP:
1. Representing Language Structure
    * E.g.: Syntatic/semantic/discourse
    * Used to train models that can generate language structures (which are used as intermediate representations/features in end-task models)
2. Capturing input/output of end-task applications
QA, IE, Summarization, etc. Used to train task-specific models.

Earlier models extracted feature from the data, and trained the modls on these feature.
[<img src="https://i.imgur.com/n6OcdWL.png" width="100%"/>]()

More recently, as neural models emerged, we have the end to end paradigm, where you feed raw text to model and the model will somehow expected to represent the syntactic etc structure, and the internal model will train on the end task. The first type of data is not needed anymore. 
[<img src="https://i.imgur.com/VlobEBL.png" width="100%"/>]()


The question is now whether such implicit representations are sufficient? Can we break E2E glass ceiling via some explicit structures? Some of theri benefits are deeper emantic undertanding, interpretability, control.

Outline of talk: Novel Type of Data for NLP
1. Modelling information struture in a (single) text
2. Modelling cros-text information relations
3. Human interaction with interactive NLP applications

Continuation of the EMNLP-2021 keynote. Refer to notes taken from EMNLP keynote.


## Dragomir R. Radev: Closing the loop in natural language interfaces to databases: Parsing, dialogue, and generation

NL interfaces for structured data, e.g.: natural language query to SQL query, table language modelling, structure to text generation (QA, summarization included) forms a closed loop. 

***SPIDER***: Complex, Cross-domain text-to-QL dataset
[<img src="https://i.imgur.com/rxCISzA.png" width="100%"/>]()


***CoQL Leaderboard***: 
***GraPPa***: Grammar-Augmented Pre-Training for Table emantic Parsing (ICLR 2021)
Yin et al. (2020) and Herzig et al. (2020) pretrain LMs on over 20M text-tables extracted from the web. 
[<img src="https://i.imgur.com/ALqFMNH.png" width="100%"/>]()


[<img src="https://i.imgur.com/9lGBvAV.png" width="100%"/>]()


[<img src="https://i.imgur.com/ViqKxwr.png" width="100%"/>]()


Synchronous Context-Free Grammar (SCFG)
[<img src="https://i.imgur.com/2T9e6Zg.png" width="100%"/>]()



Two objective functions for pretraining LMs:
1. Column Contextual Semantics (CCS)
2. Turn Contextual Switch (TCS)

[<img src="https://i.imgur.com/HPF4OmE.png" width="100%"/>]()


[<img src="https://i.imgur.com/vFCKNYI.png" width="100%"/>]()


[<img src="https://i.imgur.com/L1V5kkz.png" width="100%"/>]()
