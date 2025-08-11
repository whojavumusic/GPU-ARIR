# GPU/CUDA-based Ambisonics Impulse Response Generator
**Description:**  
GPU/CUDA-based Ambisonics Impulse Response (AIR) Generator for 3D models using a physically-based Ray Tracing algorithm.

This tool allows you to load a 3D room model, place multiple sources and receivers in 3D space, and simulate high-order Ambisonics Room Impulse Responses using GPU-accelerated ray tracing. The included GUI makes it easy to visualize and interact with your geometry, set simulation parameters, and instantly plot results.

---

![alt text]([https://github.com/whojavumusic/GPU-ARIR/blob/main/gui.png])

---

## Features

- **GPU-accelerated ray tracing** for fast simulation of sound propagation in complex 3D spaces.
- **Support for high-order Ambisonics** (user-selectable order).
- **Interactive GUI** built with PyQt and PyVista:
  - Load 3D mesh files.
  - Place multiple sound sources and receivers with sliders or manual coordinates.
  - Real-time position updates with visual feedback.
  - Grid and wireframe visualization for spatial context.
  - Automatic boundary checking with warnings when objects leave the mesh volume.
  - Adjustable Ambisonics order input.
- **RIR Visualization**:
  - Automatically plots the first channel of the simulated RIR after each run.
- **Supported Mesh Formats**: `.obj` with `.mtl` for acoustic material mapping.
- **CUDA support** for high-performance simulations (requires NVIDIA GPUs).

---

## How It Works

1. **Load a 3D Model**  
   The geometry is read into memory using PyVista/VTK.

2. **Place Sources and Receivers**  
   Define positions in Cartesian coordinates (`x, y, z`) or by dragging sliders in the GUI.

3. **Set Ambisonics Order**  
   Choose the desired Ambisonics order (e.g., `1`, `3`, `5`). Higher orders give more spatial resolution but require more computation.

4. **Run Simulation**  
   The ray tracing algorithm calculates paths, reflections, and diffractions inside the geometry.  
   The resulting impulse responses are encoded into Ambisonics format.

5. **View Results**  
   The GUI plots the first channel of the generated RIR for quick inspection.

---

## Installation

### Prerequisites

- **Operating System**: Linux only (CUDA support required for GPU acceleration).
- **Python**: 3.9+
- **NVIDIA GPU** with CUDA Toolkit installed.

### Dependencies

Install dependencies using:

```bash
pip install -r requirements.txt
