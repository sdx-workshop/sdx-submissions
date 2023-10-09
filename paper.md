---
title: 'The need for causal, low-latency sound demixing and remixing to improve accessibility'
tags:
  - separation
  - causal
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

Soundtracks and music sound different to those with hearing loss. 
Dialogue and lyrics can be difficult to pick-out and the loss of high frequencies make sounds less impactful. 
The most common treatment for hearing loss is hearing aids. 
But about 40% of people who could benefit from hearing aids do not use them often enough citing poor perceived performance. 
Being able to demix sounds on a hearing aid would allow a personalised rebalancing of sounds in a remix to improve audio quality. 
For soundtracks, you might amplify parts that are important to the narrative, such as the dialogue and key sound effects. 
For music, the requirements for remixing are still being researched but it might include amplifying the lyrics so these are easier to hear. 
A challenge is that hearing loss is heterogenious. 
Furthermore, the tolerence of hearing aid users to distortion artefacts from processing varies. 
Consequently, it is important any remix is personalised. 
The Cadenza project is running a series of machine learning challenges to improve the processing of music for those with a hearing loss. 
Our ICASSP 2024 grand demixing/remix challenge encourages causal and non-causal approaches. 
Non-causal musical source separation with deep neural networks has achieved impressive results for separating pop/rock into vocals, bass, drums, and other. 
For hearing aids and live music, a low-latency, causal approaches are needed. 
Furthermore, hearing aid processing power is limited, which is challenging for very large models. 
The paper will outline the opportunities and challenges of using source separation to improve accessibility.












