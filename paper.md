---
title: 'Self-refining of Pseudo Labels for Music Source Separation with Noisy Labeled Data'
tags:
  - separation
  - self-refining
authors:
  - name: Junghyun Koo^[co-first author] # note this makes a footnote saying 'co-first author'
    orcid: 0009-0004-4468-0367
    affiliation: 1 # (Multiple affiliations must be quoted)
  - name: Yunkee Chae^[co-first author] # note this makes a footnote saying 'co-first author'
    orcid: 0009-0000-8073-3754
    affiliation: 2
  - name: Chang-Bin Jeon
    affiliation: 1
  - name: Kyogu Lee^[corresponding author]
    orcid: 0000-0002-4210-0312
    affiliation: "1, 2, 3"
affiliations:
 - name: Department of Intelligence and Information
   index: 1
 - name: Interdisciplinary Program in Artificial Intelligence
   index: 2
 - name: Artificial Intelligence Institute, Seoul National University
   index: 3
date: 04 October 2023
bibliography: paper.bib
arxiv-doi: 10.48550/arXiv.2307.12576
---

# Abstract

Music source separation (MSS) faces challenges due to the limited availability of crrectly-labeled individual instrument tracks.
This paper proposes and automated approach for refining mislabeled instrument tracks in a partially noisy-labeled dataset.
Similar yet different from self-training \cite{xie2020self}, our approach learns directly from noisy labeled data and re-labeles the training data.
We train the classifier to perform multi-label instrument recognition with mixtures that are synthesized by randomly selecting each stem from the noisy labeled dataset.
After this training procedure, we refine the original noisy dataset with the trained classifier and use this new dataset to train the final classifier $\Psi$, which we refer to as self-refining training.
Our self-refining technique results in only a 1% accuracy degradation for multi-label instrument recognition compared to a classifier trained with a clean-labeled dataset. 
Usingthe refined multi-labeled dataset, we train the MSS models by randomly selecting stems from the dataset.
As a results, we've enhanced the MSS performance compared to the baseline, which was trained with a original noisy labeled dataset, and achieved 9th place in the leadeaboard A of the SDX challenge 2023 \cite{fabbro2023sound}.