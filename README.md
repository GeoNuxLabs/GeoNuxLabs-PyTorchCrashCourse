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