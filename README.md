# GPU/CUDA-based Ambisonics Impulse Response Generator
GPU/CUDA-based Ambisonics Impulse Response (AIR) Generator for 3D models using a physically-based Ray Tracing algorithm.

This tool allows you to load a 3D room model, place multiple sources and receivers in 3D space, and simulate high-order Ambisonics Room Impulse Responses using GPU-accelerated ray tracing. The included GUI makes it easy to visualize and interact with your geometry, set simulation parameters, and instantly plot results.

---
\
![GUI](https://github.com/whojavumusic/GPU-ARIR/blob/main/gui.jpg)

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

- The backend utilizes GSoundSIR's RayDataPipeline for the core geometric acoustic simulation, which generates essential ray data like listener directions, intensities, and time delays. It then calculates Higher Order Ambisonic (HOA) Impulse Responses using complex spherical harmonics computations and time-frequency processing, incorporating properties like time delays, intensities, and listener directions.

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


## Related Works
Currently the dataset generated using the process is in progress (https://github.com/whojavumusic/hifi-harp). The dataset can be used as plug-and-play making it easier for the researchers.

Earlier version of the dataset (with PyRoomAcoustics) is available at: https://github.com/whojavumusic/HARP and can be cited as: 

@inproceedings{saini2025harp,
  title={HARP: A Large-Scale Higher-Order Ambisonic Room Impulse Response Dataset},
  author={Saini, Shivam and Peissig, Juergen},
  booktitle={2025 IEEE International Conference on Acoustics, Speech, and Signal Processing Workshops (ICASSPW)},
  pages={1--5},
  year={2025},
  organization={IEEE}
}

This tool is built with the help of GSound, PyGSound and GSound-SIR, please cite the respective authors as follows.

@inproceedings{schissler2011gsound,
  title={Gsound: Interactive sound propagation for games},
  author={Schissler, Carl and Manocha, Dinesh},
  booktitle={Audio Engineering Society Conference: 41st International Conference: Audio for Games},
  year={2011},
  organization={Audio Engineering Society}
}

@article{schissler2017interactive,
  title={Interactive sound propagation and rendering for large multi-source scenes},
  author={Schissler, Carl and Manocha, Dinesh},
  journal={ACM Transactions on Graphics (TOG)},
  volume={36},
  number={1},
  pages={2},
  year={2017},
  publisher={ACM}
}

@misc{zang2025gsoundsirspatialimpulseresponse,
      title={GSound-SIR: A Spatial Impulse Response Ray-Tracing and High-order Ambisonic Auralization Python Toolkit}, 
      author={Yongyi Zang and Qiuqiang Kong},
      year={2025},
      eprint={2503.17866},
      archivePrefix={arXiv},
      primaryClass={cs.SD},
      url={https://arxiv.org/abs/2503.17866}, 
}




### Dependencies

Install dependencies using:

```bash
pip install -r requirements.txt
