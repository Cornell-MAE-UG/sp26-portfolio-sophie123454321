---
layout: project
title: Nutcracker Design
description: Statics and Mechanics of Solids Design Project
image: /assets/images/nutcracker-and-nut.png
---

## Problem

Design a simple lever nutcracker for macadamia nuts and find the necessary dimensions. 

---

## Constraints and Input Parameters

- Average macadamia nut diameter = 2cm  
  *(World Macadamia Organisation, 2024)*

- Average grip strength = 450N  
  *(Tomkinson et al., 2024)*

- Average load required to crack a macadamia nut = 2200N  
  *(Schrauf et al., 2008)*






---

## My Approach
The nutcracker will hinge on one end. I assumed that the part that holds the nut in place makes negligible impact on the final mechanical advantage of the system, so I ignored such protruding structures in the following calculations. 

![Nutcracker with macadamia nut]({{ "/assets/images/overall-nutcracker-FBD.png" | relative_url }}){: style="width: 400px"}

---

## Exploded FBD Calculations
![Nutcracker with macadamia nut]({{ "/assets/images/exploded-nutcracker-FBD.png" | relative_url }}){: .inline-image-r style="width: 400px"}

F nut = 2200N

F hand = 450N

∑MA = 0 = -L1 * F nut + L2 * F hand

450 L2 = 2200 L1

<b> L2 / L1 = 4.9 </b>

---

## Usability Discussion

L1 at minimum must be 1.7cm long if we want to keep the angle between the handles under 60 degrees for comfortable use. As such, L2 must be greater than or equal to 8.5cm, so the total length of the handles (after adding a few centimeters to account for the fact that we don't grip the tool by the very end) will be around 15cm long. The tool designed is the right size for a human hand.

---

## Linear Actuator Modification

![Nutcracker with macadamia nut]({{ "/assets/images/exploded-nutcracker-actuator.png" | relative_url }}){: .inline-image-r style="width: 400px"}

F nut = 2200N

F actuator = 800N

∑MA = 0 = -L1 * F nut + L2 * F actuator

<b> L2 / L1 = 2.75 </b>


If an 800N linear actuator was attached to both ends, the design can be made much smaller, although L2 can't dip below 4.7cm under the same restriction of a 60-degree angle.

Final handle length = 4.7cm / cos(π/6) =<b> 5.5cm </b>

---

## Handle Bending Analysis

Problem: Find the location of maximum elastic deflection of the handles.

Assumptions:

- Handles are experiencing pure bending
- Handles are prismatic
- Handle material is isotropic

Analysis:

1) Draw overall FBD

2) Calculate transverse loads and reactions
- Actuator_y = F_Actuator * cos(π/6) = 800 * cos(π/6) = 692.8 N
- Nut_y = F_Nut * cos(π/6) = 1905 N
- ∑F = 0 = R_y + F_Actuator - F_Nut -> R_y = 1212 N

3) Slice FBD into smaller sections, 0<x<2 and 2<x<5.5 cm


---

## Handle Cross-Section and Material Design

Problem: Choose a cross-section design and material such that the vertical elastic deflection is less than 2% of the beam's length, and is as mass-efficient as possible.



---

## Citations

Schrauf et al. Do capuchin monkeys use weight to select hammer tools, Anim Cogn 11, 413–422 (2008). https://doi.org/10.1007/s10071-007-0131-2

Tomkinson et al. (2024). International norms for adult handgrip strength: A systematic review of data on 2.4 million adults aged 20 to 100+ years from 69 countries and regions. Journal of Sport and Health Science/Journal of Sport and Health Science, 14, 101014. https://doi.org/10.1016/j.jshs.2024.101014

World Macadamia Organisation. (2024, October 17). Macadamia Style Guide, World Macadamia Organisation. (https://www.worldmacadamia.com/style-guide/)