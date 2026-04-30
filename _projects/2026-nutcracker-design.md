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

![Nutcracker beam FBD]({{ "/assets/images/nutcracker-beam-FBD.png" | relative_url }}){: .inline-image-r style="width: 400px"}

2) Calculate transverse loads and reactions
- Actuator_y = F_Actuator * cos(π/6) = 800 * cos(π/6) = <b>692.8 N</b>
- Nut_y = F_Nut * cos(π/6) = <b>1905 N</b>
- ∑F = 0 = R_y + F_Actuator - F_Nut -> R_y = <b>1212 N</b>

3) Slice FBD into smaller sections, 0≤x≤2 and 2≤x≤5.5 cm

4) Calculate internal V, M at 0≤x≤2 cm, then calculate y_1(x)
- 1212 N - V = 0 -> <b>V = 1212 N</b>
- -1212x + M = 0 -> <b>M = 1212x N-cm</b>
- EIy'' = M(x)dx
- Integrate twice to get EIy_1 = 202.1x^3 + Ax + B

5) Calculate internal V, M at 2≤x≤5.5, then calculate y_2(x)
- -V + 1212 - 1905 = 0 -> <b>V = -692.8 N</b>
- M + (x-2)(1905) - 1212x = 0 -> <b>M = -692.8x + 3811 N-cm</b>
- Integrate twice to get EIy_2 = -115.5x^3 + 1905x^2 + Cx + D

6) Use boundary conditions y_1(0) = 0, y_2(5.5) = 0, y_1(2) = y_2(2), y_1'(2) = y_2'(2) to solve for constants A, B, C, D

Final answers for y(x):

<b>EIy_1(x) = 202.1x^3 - 3637x</b>, 0≤x≤2 cm

<b>EIy_2(x) = -115.5x^3 + 1905x^2 - 7448x + 2540</b>, 2≤x≤5.5 cm

![Beam deflection diagram]({{ "/assets/images/nutcracker-y-graph.png" | relative_url }}){: .inline-image-r style="width: 400px"}

7) The maximum deflection occurs at <b>x = 2.54 cm</b>
- At this point EI*y_2(2.54) = -5980 N-cm^3

---

## Handle Cross-Section and Material Design

Problem: Choose a cross-section design and material such that the vertical elastic deflection is less than 2% of the beam's length, and is as mass-efficient as possible.

Analysis:

1) y_max ≤ 0.02 * 5.5 = 0.11 cm

2) y_max = -5980 / EI ≤ 0.11 cm
- <b>E*I ≥ 5.436 N-m^2</b>

3) Aluminum is used for the handles, as it has a decently high elastic modulus of <b>E = 69 GPa</b> for its light weight.

4) An I-beam design is used to achieve a mass-efficient design, as the goal is to resist bending by placing material as far from the neutral axis as possible.
- I = th^3/12 + bt^3/6 + bt/2 * (h+t)^2
- I ≥ 5.436 / (69 * 10^9) = 7.88 * 10^-11 m^4
- 



---

## Citations

Schrauf et al. Do capuchin monkeys use weight to select hammer tools, Anim Cogn 11, 413–422 (2008). https://doi.org/10.1007/s10071-007-0131-2

Tomkinson et al. (2024). International norms for adult handgrip strength: A systematic review of data on 2.4 million adults aged 20 to 100+ years from 69 countries and regions. Journal of Sport and Health Science/Journal of Sport and Health Science, 14, 101014. https://doi.org/10.1016/j.jshs.2024.101014

World Macadamia Organisation. (2024, October 17). Macadamia Style Guide, World Macadamia Organisation. (https://www.worldmacadamia.com/style-guide/)