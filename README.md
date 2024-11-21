# Ray Tracing with OpenMP

![Generated Image](https://github.com/JavierJimenez2/ray-tracing-with-openmp/blob/main/image.png?raw=true)

## Overview

This project was developed for the **Parallel Computing (CPA)** course (2023–2024) as part of **Lab 2**. It explores the **ray tracing technique** to generate images, starting with a sequential implementation and extending it with **parallel versions using OpenMP**.

### Key Objectives
- Implement and optimize a **parallel ray tracing algorithm**.
- Evaluate performance improvements with **OpenMP**.
- Analyze the impact of parallelization strategies on execution time and load balancing.

---

## Features

### Ray Tracing Technique
Ray tracing generates images by simulating rays of light. For each pixel in the image:
1. Rays are traced to detect object intersections.
2. The closest intersection determines the pixel's color.
3. Reflection and transparency effects are computed recursively.

The project focuses on generating images of scenes with randomly placed spheres.

### Parallelization
Two parallel versions of the ray tracing algorithm are implemented:
1. **Inner Loop Parallelization (rayp1.c)**: The x-loop of the image is parallelized.
2. **Outer Loop Parallelization (rayp2.c)**: The y-loop is parallelized, requiring synchronization for shared data.

An additional version (**rayp3.c**) introduces:
- Thread-level statistics.
- Identification of the most and least complex image lines.

### Performance Evaluation
- Execution time is measured on a cluster with varying numbers of threads.
- Different OpenMP scheduling policies (`static`, `dynamic`) are analyzed.
- Speed-ups and efficiencies are compared to determine the optimal parallel strategy.

---

## Setup and Usage

### Prerequisites
- **C Compiler**: GCC or Clang with OpenMP support.
- **OpenMP**: Installed on the system.

### Compiling
To compile the sequential version:
```bash
gcc -o ray ray0.c -fopenmp -lm
```
For the parallel versions:
```bash
gcc -o rayp1 rayp1.c -fopenmp -lm
gcc -o rayp2 rayp2.c -fopenmp -lm
gcc -o rayp3 rayp3.c -fopenmp -lm
```

### Running
Run the program with the desired number of spheres:
```bash
./ray 40
```
The output includes:
- A generated image (`untitled.ppm`).
- Complexity statistics (max/min complexity, histogram).

Example for a parallel version:
```bash
OMP_NUM_THREADS=8 ./rayp1 600
```

---

## Deliverables
- **Source Code**: Includes all versions (`ray0.c`, `rayp1.c`, `rayp2.c`, `rayp3.c`) and job files.
- **Report**: A PDF with:
  - Code modifications.
  - Results of performance tests.
  - Analysis and conclusions.

---

## Results and Performance
The generated image demonstrates the ray tracing technique, and performance improvements are observed with parallelization. Scheduling policies and thread counts significantly affect execution time and load balancing.

---

## License
This project is developed for educational purposes as part of the CPA course.
