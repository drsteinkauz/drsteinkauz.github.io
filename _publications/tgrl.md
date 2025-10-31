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
This work introduces a morphology-aware RL framework that embeds a Graph Neural Network (GNN) policy into Soft Actor-Critic (SAC). By modeling the robot’s end-caps and tendons/rods as a graph, the policy captures global coupling in tensegrity structures. The method learns three motion primitives—straight tracking and bidirectional in-place turning—achieves faster convergence and higher rewards than MLP-based baselines, and remains robust to observation noise, tendon stiffness variation, and ground slope. Policies transfer zero-shot from simulation to a physical 3-bar tensegrity robot, and primitives compose for waypoint-based navigation.