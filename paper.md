---
title: 'Separation using ChatGPT'
tags:
  - source separation
  - u-net
  - dwt
  - mra
  - noise-robust training
authors:
  - name: Nabarun Goswami # note this makes a footnote saying 'co-first author'
    orcid: 0000-0002-3960-5627
    affiliation: 1 # (Multiple affiliations must be quoted)
  - name: Tatsuya Harada^ # note this makes a footnote saying 'co-first author'
    affiliation: "1, 2"
affiliations:
 - name: The University of Tokyo, Japan
   index: 1
 - name: RIKEN, Japan
   index: 2
date: 12 October 2023
bibliography: paper.bib
---

# Abstract

Audio source separation comprises the separation of different source sounds from a mixed signal. The source signals can be slow or fast, varying with similar or contrasting frequency profiles. To solve this challenging problem, several methods have been proposed that utilize carefully designed frequency band-splitting (@luo2023music) or hybrid time-frequency domain methods (@rouard2023hybrid). In this work, we propose to use the multi-resolution analysis (MRA) capabilities of the Discrete Wavelet Transform (DWT). DWT processes the signal at several scales by successively reducing the temporal resolution and extracting the low-frequency approximation and high-frequency details at each scale.

We propose two neural network architectures to leverage the MRA: Wavelet-HTDemucs (WHTDemucs) and DWT-Transformer-UNet (DTUNet), each designed to enhance the separation of audio sources. WHTDemucs extends the HTDemucs (@rouard2023hybrid) model by introducing a third DWT branch, with the frequency branch acting as a residual bridge between the temporal and DWT branches. Meanwhile, DTUNet adopts a more simplified architecture, with independent encoders and decoders for MRA signals, complemented by a single cross-transformer to combine with the temporal branch. A source-independent post filter is applied to further enhance the output.

We also propose a noise-robust training methodology to tackle the challenge of corrupted training data, in terms of bleeding and label noise as defined by the MDX challenge (@fabbro2023sound). We combine several loss functions such as L1 loss, Mixture Consistency loss (@wisdom2020consistency), unsupervised MixIT Loss (@wisdom2020unsupervised), and Mean Teacher loss (@tarvainen2017mean), which are applied in a scheduled manner throughout the training process. We also use a model trained with the noise-robust method to filter out corrupt data from the dataset and train smaller models on the cleaned subsets. Finally, we apply ensembling and blending (@uhlich2017improving) to further boost the separation performance. We submitted our methods to the SDX 2023 challenge and achieved 2nd position in the label noise and 3rd in the bleeding leaderboards of the Music Demixing track. We also achieved 3rd position in the Cinematic Demixing track (@uhlich2023sound), competition data-only leaderboard.






