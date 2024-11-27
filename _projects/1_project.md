---
layout: page
title: Deep source separation for speech using generative models
description: Bachelor's thesis
img: 
importance: 1
category: Audio processing
related_publications: 
---

**Abstract**

Extracting the voice of desired speaker from a noisy speech is a challenging task. Speech enhancement (SE) aims to achieve this by enhancing speech that is degraded by noise. Recent studies have explored applying deep learning-based SE models for real-time usage. For instance, DeepFilterNet has been proposed for resource-constrained embedded devices, offering real-time capabilities due to its lightweight architecture. However, objective function in many of these deep neural networks is not designed to directly optimize evaluation metrics of a target task, and thus, may not always guide the networks to achieve satisfied evaluation score even if the objective loss is optimized. 

To overcome this issue, inspired by MetricGAN, we proposed to combine a metric-estimated network with DeepFilterNet2 together as a metric generative adversarial network, where the DeepFilterNet2 is seen as generator and optimized by evaluation metric. By utilizing this network structure, the estimated speech not only becomes more intelligible but is further enhanced to sound more natural. Moreover, we introduce additional distortion methods to further increase the diversity of the training data and make it more closely match noisy speech in real environments. We evaluate our proposed methods’ effectiveness by quantitatively analyzing its performance on Voice Bank + DEMAND dataset and LibriMix blind test set.


**Introduction**
Speech enhancement is a critical task involving the separation of target speech from background interference. In real-world applications, the quality and intelligibility of speech perceived by users heavily rely on the effectiveness of SE systems. These systems are critical components in contemporary automatic speech recognition (ASR), telecommunications, and hearing aid technologies. The importance of SE frameworks is highlighted by the significant volume of ongoing research aimed at improving the performance of existing SE systems. Most of these advancements utilize the latest developments in deep learning (DL) methods and the growing availability of speech data.

Common deep learning-based approaches typically determine the relationship between noisy and clean signals using discriminative methods either in the time-frequency (T-F) domain or the time domain. In T-F domain methods, the initial step involves transforming time-domain speech signals into spectral features typically using a short-time Fourier transform (STFT). The mapping from noisy to clean spectral features is established through a direct mapping function [5], or a masking function [6, 7]. The improved spectral features 4 are then reconstructed into time-domain waveforms by incorporating the phase of the noisy speech through an inverse STFT operation. In comparison to T-F domain methods, time domain methods that learn to directly map noisy to clean in waveforms, have demonstrated an ability to circumvent distortions arising from inaccurate phase information [8, 9].

In recent years, various generative approaches have been explored and proved be effectiveness for the SE task. For speech enhancement, likelihood-based models such as generative adversarial networks (GAN) [10, 11, 12, 13, 14, 15, 16], Bayesian WaveNet [17], autoregressive models [18], variational autoencoders (VAE) [19, 20], and flow-based models [21, 22] have been widely employed. Compared to discriminative approaches, generative models are more robust to unseen scenarios and tend to produce more natural speech.

In the context of utilizing GANs for SE, the process of enhancing speech involves a generator which is responsible for learning clean speech, while the discriminator plays a role in distinguishing between authentic and generated signals. By discerning real from fake signals, the discriminator conveys information to the generator. This enables the generator to learn and generate output that closely mirrors the realistic distribution of clean signals. Consequently, it helps to reconstruct the target speech from the mixed speech that has significant interference in it, where only partial information of the noisy speech is related to the clean speech.

Commonly, the objective functions used in SE are to simply estimate the $L_{p}$ norm distance between the enhanced spectrogram and the target spectrogram, as are most of the loss functions used in adversarial training. However, a smaller distance does not always mean higher speech quality. To address this issue, the MetricGAN [16] method has been proposed. In this model, the discriminator is a simple network that simulates the PESQ score. Thus, the generator is optimized directly from the evaluation metric scores that are 5 learned by the discriminator. Through this approach, the quality as well as intelligibility of speech generated by GAN-based models could be improved.

Nevertheless, many GAN-based algorithms cannot truly operate in real-time on embedded devices due to their high computational complexity, or the requirement of large time buffers for real-time use due to temporal convolutions or attention mechanisms. Both scenarios render these methods impractical for embedded devices. In response to this issue, solutions like GaGNet [23] or DeepFilterNet2 [24] have introduced smaller and more efficient architectures. This characteristic is crucial for speech enhancement (SE) on source-limited embedded devices, as system complexity must be controlled.

In this work, we proposed a GAN-based approach to improve the performance of real-time SE algorithms. Specifically, we employ DeepFilterNet2 as generator, a real-time algorithm with a lightweight framework. The discriminator of our model, on the other hand, is a simple network for predicting PESQ values using the one proposed in MetricGAN [16]. In concrete terms, we combine these two networks and perform adversarial training to exploit the following properties:

Deepfilternet could be run in real time on resource-constrained embedded devices.
Using a metric discriminator can directly connect the network's optimization objectives with audio metrics.
The generative power of GAN models.
