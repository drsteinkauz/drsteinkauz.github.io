---
title: "Morphology-Aware Graph Reinforcement Learning for Tensegrity Robot Locomotion"
header:
    teaser: "tgrl_teaser.jpg"
collection: publications
category: preprints
permalink: /publication/tgrl
excerpt: '**Chi Zhang**, Mingrui Li, Wenzhe Tong, and Xiaonan Huang'
date: 2025-10-30
venue: 'arXiv preprint, arXiv:2510.26067'
# slidesurl: ''
paperurl: 'https://arxiv.org/abs/2510.26067'
# bibtexurl: ''
# citation: ''
---
## Abstract

Tensegrity robots combine rigid rods and elastic cables, offering high resilience and deployability but posing major challenges for locomotion control due to their underactuated and highly coupled dynamics. This paper introduces a morphology-aware reinforcement learning framework that integrates a graph neural network (GNN) into the Soft Actor-Critic (SAC) algorithm. By representing the robot's physical topology as a graph, the proposed GNN-based policy captures coupling among components, enabling faster and more stable learning than conventional multilayer perceptron (MLP) policies. The method is validated on a physical 3-bar tensegrity robot across three locomotion primitives, including straight-line tracking and bidirectional turning. It shows superior sample efficiency, robustness to noise and stiffness variations, and improved trajectory accuracy. Notably, the learned policies transfer directly from simulation to hardware without fine-tuning, achieving stable real-world locomotion. These results demonstrate the advantages of incorporating structural priors into reinforcement learning for tensegrity robot control.

## Motivation

![Obstacle-aware navigation in occluded scenario](/images/tgrl_teaser.jpg)
*Figure 1: Graph-based .*

## Methodology

## Experimental Results