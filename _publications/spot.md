---
title: "SPOT: Sensing-augmented Trajectory Planning via Obstacle Threat Modeling"
header:
    teaser: "teaser_figure_spot.png"
collection: publications
category: preprints
permalink: /publication/spot
excerpt: '**Chi Zhang**<sup>*</sup>, Xian Huang<sup>*</sup>, and Wei Dong (<sup>*</sup>Equal contribution)'
date: 2025-10-18
venue: 'arXiv preprint arXiv:2510.16308'
# slidesurl: ''
paperurl: 'https://arxiv.org/abs/2510.16308'
# bibtexurl: ''
# citation: 'C. Zhang, X. Huang, and W. Dong, “Spot: Sensing-augmented trajectory planning via obstacle threat modeling,” 2025. [Online]. Available: https://arxiv.org/abs/2510.16308'
---
We introduce **SPOT**, a **sensing-augmented trajectory planning** framework that tightly couples UAV motion planning with active vision. Unlike conventional approaches that treat sensing and planning as separate tasks, SPOT explicitly incorporates perception objectives into trajectory optimization.

At its core, SPOT employs a **Gaussian Process–based obstacle belief model** to represent both observed and potential (unseen) obstacles in a unified probabilistic map. This belief is transformed into a **collision-aware observation urgency field**, guiding the UAV to not only avoid collisions but also actively seek informative viewpoints that improve future perception.

Through this joint optimization, SPOT achieves **real-time performance (<10 ms)** and enables UAVs to detect dynamic obstacles **2.8 seconds earlier** while increasing visibility by **over 500%**. Extensive simulations and real-world flights in cluttered, dynamic, and occluded environments demonstrate that SPOT delivers **safe, perception-effective navigation** by unifying motion and sensing in a single, principled framework.