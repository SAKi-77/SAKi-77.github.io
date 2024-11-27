---
layout: page
title: End-to-end Mono to Spatial Audio Generation
description: Research project at CUHK
img:
redirect: 
importance: 3
category: Audio processing
---

**This is an ongoing project at CUHK. I will share more updates once the work is published.**

**Problem Description**

This project mainly focuses on the task of sound rendering. Sound rendering involves audio spatialization, including stereo audio and spatial audio. Both are used to enhance auditory experiences. In contrast to mono audio, stereo and spatial audio convey spatial information about sound sources, enabling listeners to have a more comprehensive perception of their surroundings. More and more fields are beginning to require these immersive audio experiences, including virtual reality technology, education and entertainment. 

Traditionally, sounds in virtual environments are produced by first recording each sound source individually, followed by blending them together using various audio processing techniques according to the desired scene arrangement [2]. However, this recording process could be costly [3], requiring specialized equipment and expertise. To optimize this issue, it is essential to explore methods for generating spatial and stereo audio.

Modern generative machine learning plays a significant role in spatial/stereo audio generation, among which diffusion models [4, 5] have emerged as a novel research direction. When using these generative models to accomplish the task of generating spatial audio or stereo audio, it typically involves utilizing conditional information from different modalities, such as semantic and spatial position information, including text, melodic features, and sound source spatial locations (especially for spatial audio generation) [6, 7].

Recently, integrating audio with visual information to improve realism has gained significant attention in the field of audio spatialization. Mono2Binaural [8] utilized a custom-built stereo audio dataset and employed a U-Net architecture to encode mono audio and decode binaural audio under visual guidance. Sep-Stereo [9] generates stereo audio by integrating both audio and visual information through an associative pyramid framework. Additionally, SEE-2-SOUND [10] estimates the spatial locations of regions of interest in images and generates mono audio for these regions. Ultimately, it combines this visual information with the corresponding mono audio to create spatial audio. These studies highlight the importance of visual cues in stereo and spatial audio generation.

**Research Goal**

While the spatialization of mono audio has become a well-explored area of research, only a few works provide approaches to generate spatial audio directly [4]. This approach relates to end-to-end model training, which can simultaneously utilize content information and spatial cues to directly generate spatial audio, simplifying the training pipeline. In this project, we will focus on how to combine visual information and use end-to-end generative models to generate spatial audio. Specifically, we will attempt to generate spatialized audio samples conditioned on diverse inputs such as 3D mesh, mono audio, and/or sound source spatial position information.

Related to sound rendering, the purpose of this project is to consider solutions for generating corresponding 3D spatial audio given mono audio and related 2D image. The 3D construction of a sound field is an important topic in sound rendering. Imaging one people are listening to a concert. The sound he hears will depend on the 3D structure and reflections of the concert hall. In this research, we aim to reconstruct the 3D sound from 2D images and mono recordings. The whole process can be roughly divided into following 2 steps: 1. Extract 3D mesh from an image / 3D camera. 2. Build a neural network rendering system to take the 3D mesh and mono audio as input and output the desired sound.
