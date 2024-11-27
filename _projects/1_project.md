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

Extracting the desired speaker’s voice from a noisy speech is a challenging task. Speech enhancement (SE) aims to achieve this by enhancing speech that is degraded by noise. Recent work efforts try to apply deep-learning based SE model in real-time usage, such as DeepFilterNet, is proposed for embedded devices that is resource-constrained and realtime needed due to its lightweight architecture. However, objective function in many of these deep neural networks is not designed to directly optimize evaluation metrics of a target task, and thus, may not always guide the networks to achieve satisfied evaluation score even if the objective loss is optimized. 

To overcome this issue, inspired by MetricGAN, we proposed to combine a metric-estimated network with DeepFilterNet2 together as a metric generative adversarial network, where the DeepFilterNet2 is seen as generator and optimized by evaluation metric. By utilizing this network structure, the estimated speech not only becomes more intelligible but is further enhanced to sound more natural. Moreover, we introduce additional distortion methods to further increase the diversity of the training data and make it more closely match noisy speech in real environments. We evaluate our proposed methods’ effectiveness by quantitatively analyzing its performance on Voice Bank + DEMAND dataset and LibriMix blind test set.



