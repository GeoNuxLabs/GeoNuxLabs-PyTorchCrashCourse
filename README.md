# About This Crash Course and GeoAI Setup

This repository is part of a practical GeoAI crash course developed by GeoNuxLabs, based on a combination of several YouTube tutorials (see credits at the bottom) and insights gained through years of hands‑on experience in deep learning.

The goal of the course is to teach the fundamentals of Deep Learning and PyTorch, and then apply them to real geospatial problems such as satellite imagery analysis, raster classification, and spatial feature extraction.

Before diving into the code notebooks, this README provides the required installation steps for setting up a clean and GPU‑accelerated PyTorch environment on Ubuntu Linux.  
A correct PyTorch installation is essential for running the training notebooks efficiently, especially when working with large geospatial datasets.

This crash course is designed and tested specifically for Ubuntu Linux.  
If you're currently on Windows… well, this might be a good moment to reflect on your life choices. 
GeoAI runs smoother when your operating system isn’t actively fighting you.


The crash course is structured so that:

- this README helps you prepare your system  
- the **overview notebook** gives you a holistic conceptual understanding of how neural networks learn  
- the **step‑by‑step notebooks** dive deeper into each part of the training process with raw tensor math, PyTorch implementations, and GeoAI‑specific examples  
- the **exercises** encourage you to reflect on what you’ve learned and express it in your own words. For solutions, please see the **ExerciseAnswers notebook**. 

This structure ensures that you first understand *how neural networks work conceptually*, and then learn *how to implement them in PyTorch* for geospatial applications.

Below you will find the installation instructions for setting up the Conda environment and installing PyTorch with CUDA support.


## Installation on Ubuntu Linux (Conda + PyTorch + CUDA 12.1)

This project uses a dedicated Conda environment to ensure a clean and reproducible PyTorch setup.  
The steps below describe how to install PyTorch with full GPU acceleration on Ubuntu Linux.

### 1. Create a clean Conda environment
PyTorch does not yet support Python 3.12, so we use Python 3.10.

```bash
conda create -n pytorch python=3.10 nomkl
conda activate pytorch
```

nomkl is used to avoid Intel MKL conflicts that can cause import errors on Linux.

### 2. Install PyTorch with CUDA 12.1 (GPU support)

This uses the official PyTorch wheel index for CUDA-enabled builds.

```bash
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121
```
This installs PyTorch, TorchVision, and TorchAudio with CUDA 12.1 support.

### 3. Verify that PyTorch detects your GPU

Run the following command:
```bash
python -c "import torch; print(torch.cuda.is_available())"
```
If the output is:
```Code
True
```
then your GPU is correctly configured and ready for training.

### 4. (Optional) Install JupyterLab for running notebooks
```bash
conda install jupyterlab
```
You can now launch Jupyter with:
```bash
jupyter lab
```
### Summary

    - Uses a clean Conda environment

    - Avoids MKL/iJIT conflicts on Ubuntu

    - Installs PyTorch with CUDA 12.1 GPU acceleration

    - Fully compatible with NVIDIA GPUs on Linux

### Credits 
This crash course is inspired by the excellent PyTorch tutorial series by **Zachary Huang and **freeCodeCamp.org on YouTube. The code is rewritten, extended, and documented by GeoNuxLabs for learning purposes.