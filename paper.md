---
title: 'Separation using ChatGPT'
tags:
  - separation
  - u-net
authors:
  - name: Gerardo Roa Dabike^[corresponding author] # note this makes a footnote saying 'co-first author'
    orcid: 0000-0003-0872-7098
    affiliation: 1
  - name: Michael A. Akeroyd 
    orcid: 0000-0002-7182-9209
    affiliation: 2
  - name: Scott Bannister
    orcid: 0000-0003-4905-0511
    affiliation: 3
  - name: Jon Barker
    orcid: 0000-0002-1684-5660
    affiliation: 4
  - name: Trevor J. Cox
    orcid: 0000-0002-4075-7564
    affiliation: 1
  - name: Bruno Fazenda
    orcid: 0000-0002-3912-0582
    affiliation: 1
  - name: Jennifer Firth
    orcid: 0000-0002-7825-0945
    affiliation: 2
  - name: Simone Graetzer
    orcid: 0000-0003-1446-5637
    affiliation: 1
  - name: Alinka Greasley
    orcid: 0000-0001-6262-2655
    affiliation: 3
  - name: Rebecca Vos
    orcid: 0000-0002-2629-6271
    affiliation: 1
  - name: William Whitmer
    orcid: 0000-0001-8618-6851
    affiliation: 2
affiliations:
 - name: Acoustics Research Centre, University of Salford, UK
   index: 1
 - name: Hearing Sciences, School of Medicine, University of Nottingham, UK
   index: 2
 - name: School of Music, University of Leeds, UK
   index: 3
 - name: Department of Computer Science, University of Sheffield, UK
   index: 4
date: 06 October 2023
bibliography: paper.bib
arxiv-doi: 
---

# Abstract

Music source separation (MSS) is the task of separating a music mixture into individual sources. 
Motivated by various MSS benchmarks, several Deep Neural Network (DNN) systems have been proposed, leading to impressive results [rouard2023hybrid,kim2023sound]. 
MUSDB18 [musdb18-hq] is perhaps the most popular of these benchmarks, involving the separation of instruments, vocals, bass, drums, and the rest from a Pop/Rock song. 
These systems tend to focus on non-causal applications, such as vocal separation for karaoke applications, 
instrument separation to facilitate music transcription, and the level rebalancing of instruments in post-production. 
However, there are scenarios where music needs to be processed in real-time, making existing systems invalid. 
Applications like instrument isolation for amateur music performances or 
intelligent remixes in hearing aids for live music listening setups require causal systems that can operate in real-time and with low latency.
Therefore, we are in need of the music separation community to start considering both causal and non-causal scenarios, adapting current and new non-causal systems to causal scenarios















