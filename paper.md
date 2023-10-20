---
title: 'Zero-Shot Duet Singing Voices Separation with Diffusion Models'
tags:
  - diffusion models
  - singing voice separation
  - inverse problems
  - zero-shot learning
authors:
  - name: Chin-Yun Yu
    orcid: 0000-0003-3782-2713
    affiliation: 1
  - name: Emilian Postolache
    affiliation: 2
  - name: Emanuele Rodolà
    affiliation: 2
  - name: György Fazekas
    affiliation: 1
affiliations:
 - name: Queen Mary University of London
   index: 1
 - name: Sapienza University of Rome
   index: 2
date: 9 October 2023
bibliography: paper.bib
arxiv-doi: 10.21105/joss.01667
---

# Abstract

In recent studies, diffusion models have shown promise as priors for solving audio inverse problems [@moliner2023solving; @saito2023unsupervised; @yu2023conditioning; @murata2023gibbsddrm], including source separation [@mariani2023multi]. 
These models allow us to sample from the posterior distribution of a target signal given an observed signal by manipulating the diffusion process.
However, when separating audio sources of the same type, such as duet singing voices, the prior learned by the diffusion process may not be sufficient to maintain the consistency of the source identity in the separated audio.
For example, the singer may change from one to another from time to time.
Tackling this problem will be useful for separating sources in a choir, or a mixture of multiple instruments with similar timbre, without acquiring large amounts of paired data.
In this paper, we examine this problem in the context of duet singing voices separation, and propose a method to enforce the coherency of singer identity by splitting the mixture into overlapping segments and performing posterior sampling in an autoregressive manner, conditioning on the previous segment.
We evaluate the proposed method on the MedleyVox dataset [@jeon2023medleyvox] with different overlap ratios, and show that the proposed method outperforms naive posterior sampling baseline.
Our source code and the pre-trained model are publicly available on GitHub.
