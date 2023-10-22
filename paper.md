---
title: 'Zero-Shot Duet Singing Voices Separation with Diffusion Models'
tags:
  - diffusion models
  - singing voice separation
  - inverse problems solving
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
We evaluate the proposed method on the MedleyVox dataset [@medleyvox] with different overlap ratios, and show that the proposed method outperforms naive posterior sampling baseline.
Our source code and the pre-trained model are publicly available on GitHub.


# Introduction

With the success of audio generative models, such as OpenAI's Jukebox [@jukebox], works have been conducted to leverage them to do source separation unsupervisedly [@manilow2021unsupervised; @zai2022transfer]. The benefit of this approach is that it does not require paired data, which is sometimes difficult to obtain. Moreover, the rise of diffusion models (DMs) [@ddpm; @song2020score] introduce a more flexible way for unsupervised source separation. 

By adding conditional information into the diffusion process, we can sample the target signal from a pre-trained unconditional DMs given an observed signal. This process is called posterior sampling, and has been applied successfully in solving various audio inverse problems [@moliner2023solving; @saito2023unsupervised; @yu2023conditioning; @murata2023gibbsddrm; @vrdmg] and also source separation[@mariani2023multi; @hirano2023diffusion]. [@mariani2023multi] trained a 4-track DMs, each track correponds to $Bass$, $Drums$, $Guitar$, and $Piano$, and proposed a novel conditioning scheme based on the Dirac delta function to do  music source separation with posterior sampling. [@hirano2023diffusion] proposed to use an unconditional speech DMs to enhance an initial estimation of a multi-speaker speech separation model. They assume the target speech is draw from a Gaussian distribution centered at the initial estimation and use DDRM [@ddrm] for refining the estimation. Nevertheless, no similar work has been done on source separation of monotimbral sources, such as singing voices, solely based on a single unconditional DMs.

We start examining this problem on singing voices separation with an unconditional single singer DM and found that, without additional guidance similar to [@hirano2023diffusion], the singer identity in the separated audio is not consistent and can switch from one to another after a short period of time. This is reasonable because the prior we can use are the implicit timbre conherency and the pitch contour distribution learned by the DMs. Moreover, in case the sources in the mixture are sung by the same singer, which is common in studio recordings, only the pitch prior can be utilised. Interestingly, this kind of failure cases also exist in supervised separator [@medleyvox], showing that the problem is not trivial.

In this paper, we propose to tackle this problem by splitting the mixture into overlapping segments and perform posterior sampling sequentially. The mixture of the segment and the overlapping part of the previous segment are used as condition. We hypothesise that conditioning on the previous segment can guide the posterior sampling to maintain the singer identity. In addition, decomposing the distribution into a chain of conditional distributions also gives users more finer control over the separation process, suitable for human-in-the-loop applications. 

# Problem Formulation

# Background

# Method

# Experiments


| Methods           | SI-SDRi, 1 | SI-SDRi, 2 | SI-SDRi, 3 |
|:------:           |:----------:|:----------:|:----------:|
| AR sampling w/ TF | 3.71       | 9.45       | 11.42      |
| Naive Sampling    | 2.85       | 3.84       | 6.75       |
| AR sampling       | 2.46       | 9.64       | 11.09      | 

| Methods           | SDRi, 1 | SDRi, 2 |SDRi, 3 |
|:------:           |:-------:|:-------:|:-------:|
| AR sampling w/ TF | 4.83    | 10.18   | 11.99   |
| Naive Sampling    | 4.14    | 5.02    | 7.73    |
| AR sampling       | 3.78    | 10.34   | 11.79   |




# Conclusion

# Acknowledgements

# References