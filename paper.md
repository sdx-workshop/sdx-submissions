---
title: 'BS-RoFormer: The SAMI-ByteDance Music Source Separation System for Sound Demixing Challenge 2023'
tags:
  - music source separation
  - transformer
  - rotary position embedding
  - band-split
authors:
  - name: Ju-Chiang Wang^[co-first author]
    orcid: 0009-0002-8265-4229
    affiliation: 1 
  - name: Wei-Tsung Lu^[co-first author] # note this makes a footnote saying 'co-first author'
    affiliation: 1
  - name: Qiuqiang Kong
    orcid: 0000-0003-2864-0475
    affiliation: 1
  - name: Yun-Ning Hung
    orcid: 0000-0002-7242-6903
    affiliation: 1
affiliations:
 - name: SAMI, ByteDance Inc.
   index: 1
date: 26 September 2023
bibliography: paper.bib
arxiv-doi: 10.48550/arXiv.2309.02612
---

# Abstract

Recently, multi-band frequency-domain approaches such as Band-Split Recurrent Neural Networks (BSRNN) [@luo2023music] have been explored and achieved very promising results. In this abstract, we introduce a novel approach based on Band-Split RoPE Transformer (termed as BS-RoFormer) [@lu2023music]. Similar to BSRNN, BS-RoFormer relies on a band-split module to project the input complex spectrogram into subband-level representations. Then, instead of RNNs, we arrange a stack of hierarchical Transformers to model the inner-band as well as inter-band sequences for multi-band mask estimation. To improve the training efficacy, we use the Rotary Position Embedding (RoPE) [@su2021roformer]. The BS-RoFormer system trained on MUSDB18HQ and 500 extra songs ranked the first place in the standard MSS track (Leaderboard C) of Sound Demixing Challenge (SDX'23) [@fabbro2023sound]. It outperformed the second best by a large margin in SDR. Benchmarking our SDX'23 system on MUSDB18HQ shows state-of-the-art results, with an average SDR of 11.99 dB. In ablation study [@luo2023music], we demonstrate that a smaller version of BS-RoFormer without extra training data is also competitive, achieving an average SDR of 9.92 dB on MUSDB18HQ.
