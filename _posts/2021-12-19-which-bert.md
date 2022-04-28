---
layout: distill
title:  Which *BERT? A Survey Organizing Contextualized Encoders 
description:  short explaination of long paper 
date:   2021-12-18 00:00:00 


authors:
  - name: Albert Einstein
    url: "https://en.wikipedia.org/wiki/Albert_Einstein"
    affiliations:
      name: IAS, Princeton
  - name: Boris Podolsky
    url: "https://en.wikipedia.org/wiki/Boris_Podolsky"
    affiliations:
      name: IAS, Princeton
  - name: Nathan Rosen
    url: "https://en.wikipedia.org/wiki/Nathan_Rosen"
    affiliations:
      name: IAS, Princeton

bibliography: which-bert.bib



# Below is an example of injecting additional post-specific styles.
# If you use this post as a template, delete this _styles block.
_styles: >
  .fake-img {
    background: #bbb;
    border: 1px solid rgba(0, 0, 0, 0.1);
    box-shadow: 0 0px 4px rgba(0, 0, 0, 0.1);
    margin-bottom: 12px;
  }
  .fake-img p {
    font-family: monospace;
    color: white;
    text-align: left;
    margin: 12px 0;
    text-align: center;
    font-size: 16px;
  }

---

#   Introduction
*   Peters et. al. (2018, ELMo) won the NAACL best paper award for creating strong performing, task-agnostic sentence representations due to large scale unsupervised pretraining <d-cite key="gregor2015draw"></d-cite>. 
*   Days later, its performance was surpassed by  Radford et al. (2018) which boasted representations beyond a single sentence and finetuning flexibility
*   So, we have huge competition among models, within no time a new model comes which sets the new benchmark.
* Now, we have this question,
>   What, besides state-of-the-art, does the newest paper contribute? Also which encoder should we use?

###  Goals of this survey paper
*   Outline the areas of progress, relate contributions in text encoders to ideas from other fields
*   It is also helpful for practitioners and researchers on which encoder to choose.
*   This survey paper doesn't intend to compare specific model metrics.
*   This survey especially looks at the ideas and the progress  in the scientific discourse for text representations by distinguishing their differences.

###  This paper is organized as follows:
*   Providing brief background on encoding, training and evaluating text representations.
*   Identifying and analyzing two classes of pretraining objectives.
*   Exploring and faster and smaller models and architectures in both training and inferences.
*   Impact of both quality and quantity of pretraining data.
*   Discussing efforts on probing encoders and representations with respect to linguistic knowledge.
*   Describing the efforts into training and evaluating multilingual representations.

Publicizing **negative results** in this area is very important because we need lot of compute power, time to train these models and to ensure evaluation reproducibility. Also, probing studies need to focus not only on models and tasks but also on pretraining data.

####  Questions raised for users of contextulized encoders.
*   Whether the compute requirement of models is worth the benefits?


##  Token Prediction
* ELMo <d-cite key="peters-etal-2018-deep"></d-cite> is a BiLSTM model with a language model objective for the next (or previous) token given the forward or backward history.
* The idea of looking at the full context was further refined as cloze task (fill-in-the-blank task) or as a denoising Masked Language Modelling objective <d-cite key="devlin-etal-2019-bert"></d-cite>
  - MLM replaces some tokens with a [mask] symbol and provides both right and left contexts (bidirectional context) for predicting the masked tokens.
  - The bidirectionality is key to outperforming a unidirectional language model on a large suite of natural language understanding benchmarks. <d-cite key="devlin-etal-2019-bert"></d-cite> <d-cite key="raffel2019exploring"></d-cite>

# WILL BE UPDATED SOON.