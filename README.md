This project is a C++ program that generates and animates a 3D rotating cube using ASCII art. It demonstrates basic 3D transformations, including rotations and projections, and renders the output on the console.

## Theory

This section delves into the mathematical principles and techniques employed to achieve the 3D transformations and projections in the program.

### 3D Rotations

To animate the rotating cube, the vertices are rotated in 3D space using rotation matrices. The rotation angles \( A \), \( B \), and \( C \) represent rotations around the x, y, and z axes, respectively.

#### Rotation Matrices

- **Rotation around the x-axis**:

  ![x-axis rotation](https://latex.codecogs.com/svg.latex?%5Cbegin%7Bbmatrix%7D1%20%26%200%20%26%200%20%5C%5C0%20%26%20%5Ccos%28A%29%20%26%20-%5Csin%28A%29%20%5C%5C0%20%26%20%5Csin%28A%29%20%26%20%5Ccos%28A%29%20%5Cend%7Bbmatrix%7D)

- **Rotation around the y-axis**:

  ![y-axis rotation](https://latex.codecogs.com/svg.latex?%5Cbegin%7Bbmatrix%7D%5Ccos%28B%29%20%26%200%20%26%20%5Csin%28B%29%20%5C%5C0%20%26%201%20%26%200%20%5C%5C-%5Csin%28B%29%20%26%200%20%26%20%5Ccos%28B%29%20%5Cend%7Bbmatrix%7D)

- **Rotation around the z-axis**:

  ![z-axis rotation](https://latex.codecogs.com/svg.latex?%5Cbegin%7Bbmatrix%7D%5Ccos%28C%29%20%26%20-%5Csin%28C%29%20%26%200%20%5C%5C%5Csin%28C%29%20%26%20%5Ccos%28C%29%20%26%200%20%5C%5C0%20%26%200%20%26%201%20%5Cend%7Bbmatrix%7D)

These matrices are combined to rotate a point \( (i, j, k) \) in 3D space, creating the illusion of a rotating cube.

### 3D to 2D Projection

After rotating the points, the next step is projecting them onto a 2D plane using perspective projection. This involves calculating the 2D coordinates based on the distance from the camera to the projection plane and a scale factor \( K1 \).

#### Perspective Projection

The perspective projection transforms 3D coordinates \( (x, y, z) \) to 2D coordinates \( (xp, yp) \) using the following formulas:

- `oo𝑧` : This represents the reciprocal of the depth z. It is calculated as :
  
  ![ozz](https://latex.codecogs.com/svg.latex?ooz%20%3D%20%5Cfrac%7B1%7D%7Bz%7D)

- `xp` : This is the x-coordinate in the projected 2D space. It is calculated as:

  ![xp](https://latex.codecogs.com/svg.latex?xp%20%3D%20%5Cleft%28%20%5Cfrac%7B%5Ctext%7Bwidth%7D%7D%7B2%7D%20+%20%5Ctext%7BhorizontalOffset%7D%20+%20K1%20%5Ccdot%20%5Cfrac%7B1%7D%7Bz%7D%20%5Ccdot%20x%20%5Ccdot%202%20%5Cright%29)

- `yp` : This is the y-coordinate in the projected 2D space. It is calculated as:

  ![yp](https://latex.codecogs.com/svg.latex?yp%20%3D%20%5Cleft%28%20%5Cfrac%7B%5Ctext%7Bheight%7D%7D%7B2%7D%20+%20K1%20%5Ccdot%20%5Cfrac%7B1%7D%7Bz%7D%20%5Ccdot%20y%20%5Cright%29)

### Depth Buffer

To ensure proper rendering, a depth buffer (`zBuffer`) keeps track of the depth of each pixel on the screen. This allows closer surfaces to correctly overwrite farther surfaces, maintaining the correct visual representation of the 3D cube.

## Code Overview

The program consists of several key components, each playing a crucial role in rendering the 3D rotating cube.

1. **Global Variables**: These variables store the cube dimensions, rotation angles, buffers, and rendering settings.
2. **Functions**: 
    - `calculateX`, `calculateY`, and `calculateZ`: These functions calculate the 3D coordinates of the cube vertices.
    - `calculateForSurface`: This function projects 3D coordinates to 2D space and updates the buffer.
3. **Main Loop**: 
    - Clears the screen and buffers.
    - Calculates and projects each surface of the cube.
    - Updates the rotation angles.
    - Renders the buffer to the console.

Here’s a brief breakdown of the main functions:

### `calculateX`, `calculateY`, `calculateZ`

These functions compute the rotated coordinates for each vertex of the cube. They utilize the rotation matrices to transform the coordinates based on the current rotation angles.

### `calculateForSurface`

This function projects the 3D coordinates to 2D space, applying perspective projection. It updates the buffer and the depth buffer to ensure the correct rendering of the cube surfaces.

### Main Loop

The main loop clears the screen and buffers, then iteratively calculates the projections for each surface of the cube. It updates the rotation angles to animate the cube and renders the final ASCII art to the console.

---
