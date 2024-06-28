# 3D Rotating Cube in ASCII Art

This project is a C++ program that generates and animates a 3D rotating cube using ASCII art. It demonstrates basic 3D transformations, including rotations and projections, and renders the output on the console.

## Table of Contents
- [Introduction](#introduction)
- [Theory](#theory)
- [Code Overview](#code-overview)
- [License](#license)

## Introduction

This program displays a 3D rotating cube, rendered in ASCII art, in the console. The cube rotates continuously, providing a visual representation of 3D transformations and rendering techniques.

## Theory

This section explains the mathematical principles behind the 3D transformations and projections used in the program.

### 3D Rotations

The vertices of the cube are rotated in 3D space using rotation matrices. The rotation angles \( A \), \( B \), and \( C \) represent rotations around the x, y, and z axes, respectively.

#### Rotation Matrices

- **Rotation around the x-axis**:

  ![x-axis rotation](https://latex.codecogs.com/svg.latex?%5Cbegin%7Bbmatrix%7D1%20%26%200%20%26%200%20%5C%5C0%20%26%20%5Ccos%28A%29%20%26%20-%5Csin%28A%29%20%5C%5C0%20%26%20%5Csin%28A%29%20%26%20%5Ccos%28A%29%20%5Cend%7Bbmatrix%7D)

- **Rotation around the y-axis**:

  ![y-axis rotation](https://latex.codecogs.com/svg.latex?%5Cbegin%7Bbmatrix%7D%5Ccos%28B%29%20%26%200%20%26%20%5Csin%28B%29%20%5C%5C0%20%26%201%20%26%200%20%5C%5C-%5Csin%28B%29%20%26%200%20%26%20%5Ccos%28B%29%20%5Cend%7Bbmatrix%7D)

- **Rotation around the z-axis**:

  ![z-axis rotation](https://latex.codecogs.com/svg.latex?%5Cbegin%7Bbmatrix%7D%5Ccos%28C%29%20%26%20-%5Csin%28C%29%20%26%200%20%5C%5C%5Csin%28C%29%20%26%20%5Ccos%28C%29%20%26%200%20%5C%5C0%20%26%200%20%26%201%20%5Cend%7Bbmatrix%7D)

These matrices are combined to rotate a point \((i, j, k)\) in 3D space, creating the illusion of a rotating cube.
### 3D to 2D Projection

After rotating the points, they are projected onto a 2D plane using perspective projection. The distance from the camera to the projection plane and the scale factor \( K1 \) are used to determine the 2D coordinates.

#### Perspective Projection

The perspective projection transforms 3D coordinates \((x, y, z)\) to 2D coordinates \((xp, yp)\) using the following formulas:

\[
\text{ooz} = \frac{1}{z}
\]

\[
xp = \left(\frac{\text{width}}{2} + \text{horizontalOffset} + K1 \cdot \text{ooz} \cdot x \cdot 2\right)
\]

\[
yp = \left(\frac{\text{height}}{2} + K1 \cdot \text{ooz} \cdot y\right)
\]

### Depth Buffer

A depth buffer (\( zBuffer \)) is used to keep track of the depth of each pixel on the screen. This ensures that closer surfaces correctly overwrite farther surfaces, achieving proper rendering of the 3D cube.

## Code Overview

The program consists of the following key components:

1. **Global Variables**: These variables store the cube dimensions, rotation angles, buffer, and rendering settings.
2. **Functions**: 
    - `calculateX`, `calculateY`, and `calculateZ`: These functions calculate the 3D coordinates of the cube vertices.
    - `calculateForSurface`: This function projects 3D coordinates to 2D space and updates the buffer.
3. **Main Loop**: 
    - Clears the screen and buffers.
    - Calculates and projects each surface of the cube.
    - Updates the rotation angles.
    - Renders the buffer to the console.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

Feel free to customize the repository URL and any other specific details as per your requirements.
