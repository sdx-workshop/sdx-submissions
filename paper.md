---
title: 'Benchmarks and leaderboards for sound demixing tasks'
tags:
  - separation
  - leaderboards
  - benchmarks
authors:
  - name: Roman Solovyev^[co-first author] # note this makes a footnote saying 'co-first author'
    orcid: 0000-0003-0312-452X
    affiliation: 1
  - name: Alexander Stempkovskiy
    affiliation: 1
  - name: Tatiana Habruseva^[corresponding author]
    orcid: 0000-0003-3940-8639
    affiliation: 2
affiliations:
 - name: Institute for Design Problems in Microelectronics of Russian Academy of Sciences
   index: 1
 - name: Independent Researcher
   index: 2
date: 09 October 2023
bibliography: paper.bib
arxiv: [@solovyev2023benchmarks]
---

# Abstract

Music demixing is the task of separating different tracks from the given single audio signal into components, such as drums, bass, and vocals from the rest of the accompaniment. Separation of sources is useful for a range of areas, including entertainment and hearing aids. We introduce two new benchmarks for the sound source separation tasks and compare popular models for sound demixing, as well as their ensembles, on these benchmarks. For the models' assessments, we provide the leaderboard @qcheck, giving a comparison for a range of models. The new benchmark datasets are available for download. We also develop a novel approach for audio separation, based on the ensembling of different models that are suited best for the particular stem. The proposed solution was evaluated in the context of the Sound Demixing Challenge 2023 and achieved top results in different tracks of the challenge. The code and the approach are open-sourced on GitHub @ghubmdx. 
