# 3-DOF Robot Arm Kinematics

## Overview
This repository explores the inverse and forward kinematics of a 3 degrees of freedom (3-DOF) robot arm. The calculations provide insights into determining the end effector position from joint angles and vice versa.

## Problem Statement
The goal is to precisely calculate:
- The Cartesian coordinates (x, y, z) of the end effector given joint angles (theta1, theta2, theta3).
- The joint angles required to position the end effector at a specific Cartesian coordinate.

## Configuration
### Parameters:
- **Link Lengths**:
  - \( L_1 \): Length of the first link
  - \( L_2 \): Length of the second link
  - \( L_3 \): Length of the third link
  
- **Joint Angles**:
  - \( \theta_1 \): Angle between the base and the first link
  - \( \theta_2 \): Angle between the first and second links
  - \( \theta_3 \): Angle between the second and third links

## Forward Kinematics
### Steps to Compute End Effector Position (x, y, z):
1. Calculate the position of the wrist relative to the base frame:
   \[ x_w = L_1 \cos(\theta_1) + L_2 \cos(\theta_1 + \theta_2) + L_3 \cos(\theta_1 + \theta_2 + \theta_3) \]
   \[ y_w = L_1 \sin(\theta_1) + L_2 \sin(\theta_1 + \theta_2) + L_3 \sin(\theta_1 + \theta_2 + \theta_3) \]
   \[ z_w = L_3 \sin(\theta_3) \]

2. Compute the orientation of the wrist relative to the base frame.

## Inverse Kinematics
### Steps to Compute Joint Angles (theta1, theta2, theta3) from (x, y, z):
1. Compute the joint angle \( \theta_3 \):
   \[ \theta_3 = \sin^{-1}\left(\frac{z}{L_3}\right) \]

2. Compute the joint angles \( \theta_1 \) and \( \theta_2 \):
   - Calculate \( r = \sqrt{x^2 + y^2} - L_1 \)
   - Compute \( \beta = \tan^{-1}\left(\frac{z}{r}\right) \)
   - Calculate \( \alpha = \tan^{-1}\left(\frac{y}{x}\right) \)
   - Determine \( \gamma = \cos^{-1}\left(\frac{L_2^2 + r^2 - L_3^2}{2 L_2 r}\right) \)
   - Finally, obtain \( \theta_1 \) and \( \theta_2 \) as:
     \[ \theta_1 = \alpha - \beta \]
     \[ \theta_2 = \gamma \]

## Example Calculation
### Given:
- \( L_1 = 10 \) cm
- \( L_2 = 15 \) cm
- \( L_3 = 8 \) cm
- Desired end effector position: \( (x, y, z) = (12, 18, 6) \)

### Steps:
1. **Inverse Kinematics Calculation**:
   - Calculate \( \theta_3 \):
     \[ \theta_3 = \sin^{-1}\left(\frac{6}{8}\right) = \sin^{-1}(0.75) \approx 48.59^\circ \]

2. Calculate \( r \):
   \[ r = \sqrt{12^2 + 18^2} - 10 = \sqrt{144 + 324} - 10 = \sqrt{468} - 10 \approx 5.39 \]

3. Calculate \( \beta \):
   \[ \beta = \tan^{-1}\left(\frac{6}{5.39}\right) \approx \tan^{-1}(1.11) \approx 48.84^\circ \]

4. Calculate \( \alpha \):
   \[ \alpha = \tan^{-1}\left(\frac{18}{12}\right) \approx \tan^{-1}(1.5) \approx 56.31^\circ \]

5. Calculate \( \gamma \):
   \[ \gamma = \cos^{-1}\left(\frac{15^2 + 5.39^2 - 8^2}{2 \cdot 15 \cdot 5.39}\right) \approx \cos^{-1}(0.724) \approx 43.42^\circ \]

6. Finally, compute \( \theta_1 \) and \( \theta_2 \):
   \[ \theta_1 = 56.31^\circ - 48.84^\circ \approx 7.47^\circ \]
   \[ \theta_2 = 43.42^\circ \]

### Forward Kinematics:
- Plug in \( \theta_1, \theta_2, \theta_3 \) values into the forward kinematics equations to verify the end effector position.

## Conclusion
This repository offers a detailed exploration of 3-DOF robot arm kinematics, providing comprehensive steps and algorithms for calculating both forward and inverse kinematics. By understanding these principles, engineers and enthusiasts can design and control robotic systems with precision and efficiency.
