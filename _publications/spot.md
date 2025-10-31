---
title: "SPOT: Sensing-augmented Trajectory Planning via Obstacle Threat Modeling"
header:
    teaser: "spot_pipeline.png"
collection: publications
category: preprints
permalink: /publication/spot
excerpt: '**Chi Zhang**<sup>*</sup>, Xian Huang<sup>*</sup>, and Wei Dong (<sup>*</sup>Equal contribution)'
date: 2025-10-18
venue: 'arXiv preprint, arXiv:2510.16308'
# slidesurl: ''
paperurl: 'https://arxiv.org/abs/2510.16308'
# bibtexurl: ''
# citation: 'C. Zhang, X. Huang, and W. Dong, “Spot: Sensing-augmented trajectory planning via obstacle threat modeling,” 2025. [Online]. Available: https://arxiv.org/abs/2510.16308'
---
## Abstract

UAVs equipped with a single depth camera encounter significant challenges in dynamic obstacle avoidance due to limited field of view and inevitable blind spots. While active vision strategies that steer onboard cameras have been proposed to expand sensing coverage, most existing methods separate motion planning from sensing considerations, resulting in less effective and delayed obstacle response. To address this limitation, we introduce SPOT (Sensing-augmented Planning via Obstacle Threat modeling), a unified planning framework for observation-aware trajectory planning that explicitly incorporates sensing objectives into motion optimization. At the core of our method is a Gaussian Process-based obstacle belief map, which establishes a unified probabilistic representation of both recognized (previously observed) and potential obstacles. This belief is further processed through a collision-aware inference mechanism that transforms spatial uncertainty and trajectory proximity into a time-varying observation urgency map. By integrating urgency values within the current field of view, we define differentiable objectives that enable real-time, observation-aware trajectory planning with computation times under 10 ms. Simulation and real-world experiments in dynamic, cluttered, and occluded environments show that our method detects potential dynamic obstacles 2.8 seconds earlier than baseline approaches, and enabling safe navigation through cluttered, occluded environments.

## Motivation

For obstacle-aware navigation in a dynamic and occluded environment, it is necessary for the UAV to actively adject its trajectory to reveal occluded threats. Therefore, the UAV trajectory planner should hold a balance between obstacle avoidance and viewpoints optimization. To enable a principle evaluation of the viewpoints for obstacle-aware navigation, a unified probabilistic obstacle model that can consider both observed and unobserved dynamic obstacles within the same decision process remains necessary.

![Obstacle-aware navigation in occluded scenario](/images/spot_motivation.png)
*Figure 1: Comparison between uncoupled and sensing-augmented planner in occluded scenario.*

## Methodology

We introduce **SPOT**, a **sensing-augmented trajectory planning** framework that tightly couples UAV motion planning with active vision. Unlike conventional approaches that treat sensing and planning as separate tasks, SPOT explicitly incorporates perception objectives into trajectory optimization.

At its core, SPOT employs a **Gaussian Process–based obstacle belief model** to represent both observed and potential (unseen) obstacles in a unified probabilistic map. This belief is transformed into a **collision-aware observation urgency field**, guiding the UAV to not only avoid collisions but also actively seek informative viewpoints that improve future perception.

![Pipeline overview of SPOT](/images/teaser_figure_spot_1.png)
*Figure 2: Overview of the SPOT pipeline*

## Experimental Results

To verify the effectiveness of SPOT, 3 dynamic environments were designed:
* **Street**: An outdoor straight path with moving pedestrians;
* **Museum**: An indoor maze-like environment with long corridors and occlusions;
* **Corner**: A corner-shaped corridor where dynamic obstacles appear suddenly from behind the wall.

We benchmarked 4 planners:
* **SPOT**: Full sensor-augmented planning with urgency-driven cost;
* **SPOT<sup>*</sup>**: SPOT with $\lambda_v = 0$, removing the urgency term;
* **EGO-Planner**: Baseline motion planning without sensing objectives;
* **AASA + EGO-Planner**: Active sensing with decoupled motion planning.

Performance was evaluated using three metrics:
* **Success ratio**: The percentage of collision-free trials;
* **Observation lead time**: The time difference between the first observation of a dynamic obstacle and its entry within distance threshold $d_f$;
* **Observation time coverage ratio**: The percentage of time a dynamic obstacle remains in view while within $d_f$.

![Benchmarking performance in diverse scenarios](/images/spot_result_1.png)
*Figure 3: Benchmarking performance in diverse scenarios: (a) street. (b) corner. (c) museum.*

SPOT outperforms the baselines, detects potential dynamic obstacles earlier while remaining time coverage, and achieves higher success ratio.