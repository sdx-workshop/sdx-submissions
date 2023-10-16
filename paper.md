---
title: 'The Mixology Dataset'
tags:
  - dataset
  - mixing
  - parameter recommendation
  - digital audio workstation
authors:
  - name: Michael Clemens
    orcid: 0000-0002-4507-8421
    affiliation: 1
affiliations:
 - name: University of Utah
   index: 1
date: 15 October 2023
bibliography: paper.bib
---

# Abstract

Generative artificial intelligence (AI) is making strides in AI music, but its effectiveness largely depends on the diversity of audio samples from various genres. The transparency of the datasets used by many successful models has sparked concerns among artists about the legality of the music data used for training. As generative AI models require more data for improved performance, the challenge lies in ethically sourcing this data while adhering to the music industry's licensing rules.

While there is a significant lack of large, open-source audio datasets for training, the scarcity is even more pronounced when it comes to data for mixing and mastering tasks in music production. Often, parameter values are confined within the digital audio workstation and are not made publicly available. To address these gaps, we introduce **The Mixology Dataset**, an extension of Brecht De Man et al.'s *The Mixing Evaluation* dataset \cite{de2017mix}. Our dataset offers individual track and plugin settings for 114 mixes spanning 34 songs. It includes details such as *gain*, *pan*, *equalization*, *compression*, and *reverb* settings for each track, all structured within a JSON format.

The licensing terms of each song are maintained, and parameter values were collected only from non-copyrighted songs. We recommend using the AI2 ImpACT-LR License \cite{AI2ImpAC53} for all artifacts generated using this dataset. Additionally, we provide a tool that can systematically extract parameter values from images of plugin screenshots. We hope this contribution will aid in developing co-creative agents for assisted mixing and mastering.

