# PyTorch Wheels for DGX Spark

**Architecture:** aarch64 • **Python:** 3.10 • **CUDA:** 13.0

This repository contains backup copies of **PyTorch**, **Torchvision**, **Torchaudio**, and related dependency wheels confirmed working on an **NVIDIA DGX Spark** system.

---

## System Configuration (Verified)

| Component         | Details                                        |
| ----------------- | ---------------------------------------------- |
| **Hardware**      | NVIDIA DGX Spark (Blackwell GB10 GPU, aarch64) |
| **OS**            | Ubuntu 24.04.3 LTS                             |
| **Python**        | 3.10.14 (via pyenv)                            |
| **CUDA Toolkit**  | 13.0 (installed via `apt`)                     |
| **NVIDIA Driver** | 580.95.05                                      |
| **Date Verified** | October 25, 2025                               |

---

## Purpose

This repository serves as a **backup** of specific wheel files in case:

* the official download source becomes unavailable, or
* an **offline installation** is required.

> **Note:** When possible, always prefer installing from the official PyTorch index using `pip`.

---

## Included Files

This repository includes wheel files for:

* `torch-2.9.0+cu130-cp310-cp310-manylinux_2_28_aarch64.whl`
* `torchvision-0.24.0-cp310-cp310-manylinux_2_28_aarch64.whl`
* `torchaudio-2.9.0-cp310-cp310-manylinux_2_28_aarch64.whl`
* Supporting dependencies (e.g., `numpy`, `nvidia-*`) downloaded together using:

```bash
pip download --index-url https://download.pytorch.org/whl/cu130
```

---

## Installation from Local Wheels

### ⚠️ Important: Git LFS Required

These wheels are **large (hundreds of MB)** and stored via **Git Large File Storage (LFS)**.

Before cloning:

```bash
sudo apt install git-lfs     # or your distro's equivalent
git lfs install --system
```

---

## Installation Steps

### 1. Ensure prerequisites

Your target system should match the configuration listed above—especially:

* Python **3.10**
* CUDA **13.0**

---

### 2. Clone the repository

```bash
git clone <repo-url>
```

Git LFS will automatically download the real wheel files.

---

### 3. Install wheels

Activate your Python 3.10 environment and run:

```bash
# (optional) install base dependencies first
pip install numpy-*.whl
pip install nvidia_*.whl

# install PyTorch and related packages
pip install torch-*.whl torchvision-*.whl torchaudio-*.whl

# install any remaining dependencies
pip install *.whl
```

> Adjust order if dependency errors occur.

---

## Verify Installation

```bash
python -c "import torch; print('PyTorch version:', torch.__version__); print('CUDA available:', torch.cuda.is_available())"
```

Expected output:

* Correct PyTorch version
* `CUDA available: True`

---

## Disclaimer

These files are provided **as-is**, with no warranty.
For the most up-to-date and secure installations, always use the official PyTorch distribution channels when available.
