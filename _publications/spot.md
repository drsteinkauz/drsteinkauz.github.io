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
UAVs equipped with a single depth camera face major challenges in dynamic obstacle avoidance due to limited field of view and blind spots. Existing active vision methods that steer onboard cameras often separate motion planning from sensing considerations, leading to delayed obstacle responses. To address this limitation, we present **SPOT** (**S**ensing-augmented **P**lanning via **O**bstacle **T**hreat modeling), a unified framework for observation-aware trajectory planning that integrates sensing objectives directly into motion optimization. Central to SPOT is a Gaussian Process–based obstacle belief map that models both recognized and potential obstacles within a single probabilistic representation. A collision-aware inference mechanism then converts spatial uncertainty and trajectory proximity into a time-varying observation urgency map, enabling real-time, differentiable trajectory optimization (<10 ms). Simulation and real-world results demonstrate that SPOT detects dynamic obstacles 2.8 s earlier than baselines, achieving safer navigation in cluttered, occluded environments.

## Motivation

For obstacle-aware navigation in dynamic and partially occluded environments, the UAV must actively adjust its trajectory to uncover potential hidden threats. Therefore, the trajectory planner needs to strike a balance between obstacle avoidance and viewpoint optimization. To enable a principled evaluation of viewpoints for obstacle-aware navigation, a unified probabilistic obstacle model is required, one that can account for both observed and unobserved dynamic obstacles within a single decision-making framework.

![Obstacle-aware navigation in occluded scenario](/images/spot_motivation.png)
*Figure 1: Comparison between uncoupled and sensing-augmented planner in occluded scenario.*

## Methodology

We introduce **SPOT**, a **sensing-augmented trajectory planning** framework that tightly couples UAV motion planning with active vision. Unlike conventional approaches that treat sensing and planning as separate tasks, SPOT explicitly incorporates perception objectives into trajectory optimization.

At its core, SPOT employs a **Gaussian Process–based obstacle belief model** to represent both observed and potential (unseen) obstacles in a unified probabilistic map. This belief is transformed into a **collision-aware observation urgency field**, guiding the UAV to not only avoid collisions but also actively seek informative viewpoints that improve future perception.

![Pipeline overview of SPOT](/images/spot_pipeline.png)
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

SPOT outperforms baseline methods by detecting potential dynamic obstacles earlier, maintaining timely coverage, and achieving a higher success rate.

![Benchmarking performance in corner scenarios](/images/spot_result_2.png)
*Figure 4: Trajectory comparison in a simple corner environment: (a) Gazebo simulation environment (b) EGO-Planner's trajectory resulting in collision with the obstacle. (c) SPOT's trajectory demonstrating successful obstacle avoidance.*