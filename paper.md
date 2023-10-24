---
title: 'StemGMD: A Large-Scale Multi-Kit Audio Dataset for Deep Drums Demixing'
tags:
  - drums
  - demixing
  - separation
  - dataset
  - u-net
authors:
  - name: Alessandro Ilic Mezza^[corresponding author]
    orcid: 0000-0002-9438-3190
    affiliation: 1
  - name: Riccardo Giampiccolo
    orcid: 0000-0001-6144-8288
    affiliation: 1
  - name: Alberto Bernardini
    orcid: 0000-0001-7973-0134
    affiliation: 1
  - name: Augusto Sarti
    orcid: 0000-0002-5803-1702
    affiliation: 1
affiliations:
 - name: Image and Sound Processing Lab, Politecnico di Milano 
   index: 1
date: 28 September 2023
bibliography: paper.bib
---

# Abstract

In music demixing, drums is conventionally treated as a single stem despite being an ensemble of percussive 
instruments in itself. At the same time, the availability of publicly-available datasets specifically 
tailored for drums demixing has been severely lacking. To address this gap, we present StemGMD[^1], the first large-scale 
multi-kit audio dataset of isolated single-instrument drum stems. Each audio clip in StemGMD is synthesized from MIDI 
recordings of expressive drums performances taken from Magenta's Groove Midi Dataset (GMD) using ten real-sounding sample libraries from Logic Pro X.
Totaling over 1224 hours, StemGMD is the largest dataset of drums to date and the first to comprise isolated 
audio clips for every instrument in a canonical nine-piece drum kit, i.e., kick drum, snare, high tom, mid-low tom, floor tom, open hi-hat, closed hi-hat, ride cymbal, crash cymbal.
StemGMD also contains single hits for each drum piece at varying velocities, and is inherently aligned with the MIDI 
content and metadata found in GMD, allowing for a broad range of applications such as Automatic Drum Transcription. 
Furthermore, having access to isolated audio stems enables a vast array of diverse data augmentation methods that draw 
inspiration from common music production practices. Alongside the dataset, we release a reference model built upon a 
bank of parallel U-Nets that separates five stems (kick drum, snare, tom-toms, hi-hat, cymbals) from a stereo drum mixture through spectro-temporal soft masking. 
Such model is meant to serve as a baseline for future research and might complement existing music demixing models.

[^1] DOI: 10.5281/zenodo.7860223