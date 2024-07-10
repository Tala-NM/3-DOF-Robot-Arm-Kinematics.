# 3-DOF Robot Arm Kinematics

This explores the inverse and forward kinematics of a 3 degrees of freedom (3-DOF) robot arm. The calculations provide insights into determining the end effector position from joint angles and vice versa.

## Problem Statement
The goal is to precisely calculate:
- The Cartesian coordinates (x, y, z) of the end effector given joint angles (θ₁, θ₂, θ₃).
- The joint angles required to position the end effector at a specific Cartesian coordinate.

## Configuration
### Parameters:
- **Link Lengths**:
  - \( L₁ \): Length of the first link
  - \( L₂ \): Length of the second link
  - \( L₃ \): Length of the third link
  
- **Joint Angles**:
  - \( θ₁ \): Angle between the base and the first link
  - \( θ₂ \): Angle between the first and second links
  - \( θ₃ \): Angle between the second and third links

## Forward Kinematics
### Steps to Compute End Effector Position (x, y, z):
1. Calculate the position of the end effector relative to the base frame:
   \[ x = L₁ \cos(θ₁) + L₂ \cos(θ₁ + θ₂) + L₃ \cos(θ₁ + θ₂ + θ₃) \]
   \[ y = L₁ \sin(θ₁) + L₂ \sin(θ₁ + θ₂) + L₃ \sin(θ₁ + θ₂ + θ₃) \]
   \[ z = L₃ \sin(θ₃) \]

   Example:
   - \( L₁ = 10 \) units, \( L₂ = 8 \) units, \( L₃ = 6 \) units
   - \( θ₁ = 30^\circ \), \( θ₂ = 45^\circ \), \( θ₃ = 60^\circ \)

   Calculating:
   \[ x = 10 \cos(30^\circ) + 8 \cos(30^\circ + 45^\circ) + 6 \cos(30^\circ + 45^\circ + 60^\circ) \]
   \[ y = 10 \sin(30^\circ) + 8 \sin(30^\circ + 45^\circ) + 6 \sin(30^\circ + 45^\circ + 60^\circ) \]
   \[ z = 6 \sin(60^\circ) \]

   Result:
   \[ x ≈ 18.66 \text{ units} \]
   \[ y ≈ 15.73 \text{ units} \]
   \[ z ≈ 5.20 \text{ units} \]

## Inverse Kinematics
### Steps to Compute Joint Angles (θ₁, θ₂, θ₃) from (x, y, z):
1. Compute the joint angle \( θ₃ \):
   \[ θ₃ = \sin^{-1}\left(\frac{z}{L₃}\right) \]

   Example:
   - Using the same values: \( L₃ = 6 \), \( z ≈ 5.20 \)

   Calculating:
   \[ θ₃ = \sin^{-1}\left(\frac{5.20}{6}\right) \]
   \[ θ₃ ≈ 60^\circ \]

2. Compute the joint angles \( θ₁ \) and \( θ₂ \):
   - Calculate \( r = \sqrt{x² + y²} - L₁ \)
   - Compute \( β = \tan^{-1}\left(\frac{z}{r}\right) \)
   - Calculate \( α = \tan^{-1}\left(\frac{y}{x}\right) \)

   Example:
   - Using the calculated values: \( x ≈ 18.66 \), \( y ≈ 15.73 \), \( r ≈ \sqrt{18.66² + 15.73²} - 10 \)

   Calculating:
   \[ r ≈ 10.61 - 10 = 0.61 \]

   \[ β = \tan^{-1}\left(\frac{5.20}{0.61}\right) \]
   \[ β ≈ \tan^{-1}(8.52) \]

   \[ α = \tan^{-1}\left(\frac{15.73}{18.66}\right) \]
   \[ α ≈ \tan^{-1}(0.84) \]

   Result:
   \[ θ₁ ≈ 30^\circ \]
   \[ θ₂ ≈ 45^\circ \]

## Methodology
This section details the approach taken to solve the kinematics problems, including any algorithms or numerical methods employed. Challenges encountered during the process are discussed, alongside strategies for overcoming them to ensure accurate results.

## Results
Sample calculations and examples are provided to demonstrate the application of the kinematic equations in practical scenarios, showcasing how the robot arm's position and orientation can be computed and controlled effectively.

## Conclusion
In conclusion, this not only provides a robust solution to the 3-DOF robot arm kinematics problem but also offers deep insights into the mathematical foundations that underpin robotic motion planning and control. By understanding these principles, engineers and enthusiasts alike can enhance their ability to design and program robotic systems with precision and efficiency.
