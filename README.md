PyTorch Wheels for DGX Spark (aarch64 / Python 3.10 / CUDA 13.0)

This repository contains backup copies of PyTorch, Torchvision, TorchAudio wheel files (.whl) and their dependencies that were confirmed working on an NVIDIA DGX Spark system with the following configuration:

Hardware: NVIDIA DGX Spark (Blackwell GB10 GPU, aarch64 architecture)

Operating System: Ubuntu 24.04.3 LTS

Python: 3.10.14 (Managed via pyenv)

CUDA Toolkit: 13.0 (Installed via apt)

NVIDIA Driver: 580.95.05

Date Verified: October 25, 2025

Purpose

These files serve as a backup in case the specific combination becomes unavailable from the official download sources or if offline installation is required. The primary method should always be to install directly using pip and the appropriate index URL.

Files Included

This repository contains the wheel files for:

torch-2.9.0+cu130-cp310-cp310-manylinux_2_28_aarch64.whl

torchvision-0.24.0-cp310-cp310-manylinux_2_28_aarch64.whl

torchaudio-2.9.0-cp310-cp310-manylinux_2_28_aarch64.whl

Associated dependencies (numpy, nvidia-*, etc.) downloaded during the same pip download operation.

Source: The files were originally downloaded using pip download --index-url https://download.pytorch.org/whl/cu130.

Installation from Local Wheels

IMPORTANT: These wheel files are very large (several hundred MB each). This repository uses Git Large File Storage (LFS). You must have Git LFS installed on your system before cloning to download the actual wheel files instead of just pointers.

Install Git LFS: If you don't have it, install it (e.g., sudo apt install git-lfs on Debian/Ubuntu) and run git lfs install --system once.

Ensure Prerequisites: Make sure your target system matches the configuration listed above (especially Python 3.10 and CUDA 13.0).

Clone Repository: Clone this repository using git clone <repo-url>. Git LFS should automatically download the large wheel files during the clone process.

Navigate to Directory: Open a terminal in the directory containing the .whl files.

Install: Use pip to install the wheels. It's often best to install PyTorch first, then the others. You might need to install dependencies manually or let pip handle them if network access is available. A simple approach is:

# Ensure your Python 3.10 environment is active
pip install numpy-*.whl # Install numpy first if needed by others
pip install nvidia_*.whl # Install NVIDIA helper libraries
pip install torch-*.whl torchvision-*.whl torchaudio-*.whl
pip install *.whl # Install remaining dependencies


(Adjust the order if dependency errors occur.)

Verify Installation:

python -c "import torch; print(f'PyTorch version: {torch.__version__}'); print(f'CUDA available: {torch.cuda.is_available()}')"


The output should show the correct version and CUDA available: True.

Disclaimer

These files are provided as-is without warranty. Always prefer installing packages from official sources (pip install with index URLs) when possible.