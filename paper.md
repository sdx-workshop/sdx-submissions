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

With the success of audio generative models, such as OpenAI's Jukebox [@jukebox], works have been conducted to leverage them to do source separation unsupervisedly [@manilow2021unsupervised; @zai2022transfer].
The benefit of this approach is that it does not require paired data, which is sometimes difficult to obtain.
Moreover, the rise of diffusion models (DMs) [@ddpm; @song2020score] introduce a more flexible way for unsupervised source separation.


By adding conditional information into the diffusion process, we can sample the target signal from a pre-trained unconditional DM given an observed signal.
This process is called posterior sampling, and has been applied successfully in solving various audio inverse problems [@moliner2023solving; @saito2023unsupervised; @yu2023conditioning; @murata2023gibbsddrm; @vrdmg] and also source separation[@mariani2023multi; @hirano2023diffusion].
[@mariani2023multi] trained a 4-track DM, each track correponds to $Bass$, $Drums$, $Guitar$, and $Piano$, and proposed a novel conditioning scheme based on the Dirac delta function to do music source separation with posterior sampling.
[@hirano2023diffusion] proposed to use an unconditional speech DM to enhance an initial estimation of a multi-speaker speech separation model.
They assume the target speech is draw from a Gaussian distribution centered at the initial estimation and use DDRM [@ddrm] for refining the estimation.
Nevertheless, no similar work has been done on source separation of monotimbral sources, such as singing voices, solely based on a single unconditional DM.

We start examining this problem on singing voices separation with an unconditional single singer DM and found that, without additional guidance similar to [@hirano2023diffusion], the singer identity in the separated audio is not consistent and can switch from one to another after a short period of time.
This is reasonable because the prior we can use are the implicit timbre conherency and the pitch contour distribution learned by the DMs.
Moreover, in case the sources in the mixture are sung by the same singer, which is common in studio recordings, only the pitch prior can be utilised.
Interestingly, this kind of failure cases also exist in supervised separator [@medleyvox], showing that the problem is not trivial.

In this paper, we propose to tackle this problem by splitting the mixture into overlapping segments and perform posterior sampling sequentially.
The mixture of the segment and the overlapping part of the previous segment are used as condition.
We hypothesise that conditioning on the previous segment can guide the posterior sampling to maintain the singer identity.
In addition, decomposing the distribution into a chain of conditional distributions also gives users more finer control over the separation process, suitable for human-in-the-loop applications.


# Problem Formulation

Let us start with a general formulation of the multi-channel audio inverse problem.
We have an M-channel mixture signal $\mathbf{x}(n, f) \in \mathbb{C}^M$ where $n, f$ are the time and frequency indices, respectively.
It contains $N$ sources $s_i(n, f) \in \mathbb{C}^N$ where $i \in \{1, 2, ..., N\}$, and a measurement noise signal $z \sim CN(0, \sigma_x^2)$.
The sources are transformed by a non-invertible linear system $\mathbf{H}(n, f) \in \mathbb{C}^{M \times N}$ and mixed with the noise, resulting in
$$
\mathbf{x}(n, f) = \mathbf{H}(n, f)
\begin{bmatrix}
s_1(n, f) \\
s_2(n, f) \\
\vdots \\
s_N(n, f)
\end{bmatrix}
+ z.
$$
The objective of the inverse problem is to estimate the sources $\mathbf{s}(n, f) \in \mathbb{C}^N$ from the mixture $\mathbf{x}(n, f)$.
To solve this unsupervisedly with posterior sampling, we need to train DMs that model the distribution of the sources $p(s_i(n, f))$.
Each $s_i(n, f)$ is either drawn from different or the same distributions (DMs), where the latter is the case we want to tackle in this paper.
Note that by distribution we mean the same instrument, such as singing voices and strings, as monotimbral sources.

## Related works

The work by [@mariani2023multi] is one of the pioneer that use posterior sampling to do source separation. 
They consider single channel source separation with $\mathbf{H}(n, f)$ is simply an all-one vector.
However, they modelled the joint distribution $p(s_1(n, f), s_2(n, f), \cdots, s_N(n, f))$ with a single DM and utilise the inter-source correlation to do separation. 
The joint-training method also cannot generalise arbitrary number of sources.
[@hirano2023diffusion] is the closest work to ours.
The DM they used is trained on single speaker speech data, but the requirement of a pre-trained speech separation model breaks the fully unsupervised assumption.

Outside source separation, several works have dealt with this problem with a single source ($N=1$), either with a known $\mathbf{H}(n, f)$ in the case of bandwidth extension [@moliner2023solving; @yu2023conditioning; @vrdmg] or an unknown one such as removing reverberation from vocals [@murata2023gibbsddrm, @saito2023unsupervised].
Non-linear problems such as de-cliping [@moliner2023solving; @vrdmg] has also been tackled with DMs.

Lastly, we want to point out that, there are no works, to the best of our knowledge, that use this approach to solve problems with multiple sources and multi-channel mixtures, either the $\mathbf{H}(n, f)$ is known or unknown.
This problem occurs in ensemble separation, such as choir or orchestra sections, which is often recorded with multiple microphones.
The holy grail of this approach is to have a generalised solution that can be applied on arbitrary transformation $\mathbf{H}(n, f)$ and $N$ with the same set of DMs, and each of the DMs is trained on isolated sources without the need of mixture data.

# Methodology

In diffusion models, the data generation process is governed by an ODE
$$
d\mathbf{s}(t) = \sigma(t) \nabla_{\mathbf{s}(t)} \log p(\mathbf{s}(t)) dt.
$$
Here, we use $\mathbf{s}(t)$ to represent $s_i(n, f) + z, z \sim N(0, \sigma^2(t))$ for arbitrary $i$.
The $\sigma(t)$ is a increasing function of $t$ and is called the noise schedule.
Because $\mathbf{s}(0) \approx s_i(n, f)$, we can sample them by integrating the ODE from $t=T$ to $t=0$ with $\mathbf{s}(T) \sim N(\mathbf{0}, \sigma^2(T))$.
We can use a neural network $\theta(\mathbf{s}(t); t)$ to estimate the score function $\nabla_{\mathbf{s}(t)} \log p(\mathbf{s}(t))$ by training them to denoise the noisy data $\mathbf{s}(t)$, where $t \sim U(0, T)$.


## Mixture conditioning

One can transform the score function to a conditional one using simple bayes rule
$$
\nabla_{\mathbf{s}(t)} \log p(\mathbf{s}(t)|\mathbf{x}) = \nabla_{\mathbf{s}(t)} \log p(\mathbf{x}|\mathbf{s}(t)) + \nabla_{\mathbf{s}(t)} \log p(\mathbf{s}(t)).
$$
We consider the simple case where the mixture is simply a sum of the sources, i.e. $\mathbf{x} = \sum_{i = 1}^N \mathbf{s}_i(0)$.
We choose the weakly-supervised posterior score function from [@mariani2023multi] as our conditional score function, which is

$$
\nabla_{\mathbf{s}_i(t)} \log p(\mathbf{s}_i(t)|\mathbf{x}) \approx
\nabla_{\mathbf{s}_i(t)} \log p(\mathbf{s}_i(t)) - 
\nabla_{\mathbf{s}_i(t)} \log p(\mathbf{x} - \sum_{i = 2}^N \mathbf{s}_i(t))
$$
for $i > 1$ and we set $\mathbf{s}_1(t)$ as the constrained source.

## Enforcing coherency with autoregressive inpainting

To tackle the problem of singer identity switching, we propose to split the mixture into overlapping segments and perform posterior sampling sequentially.
The mixture of the segment and the overlapping part of the previous separated segment are used as condition.
The conditioning is simply placing the noisy $\mathbf{s}(t)$ condition on the overlapping part during sampling, similar to doing inpainting [@crash].
This regulates the model to predict more coherent signal to the condition in the non-overlapping part.
The whole sampling process is illustrated in Figure \ref{fig:diagram}.

![A diagram of the conditioning process on two consecutive segments.\label{fig:diagram}](figures/diagram.png){width=80%}


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




# Conclusions

# Acknowledgements

# References