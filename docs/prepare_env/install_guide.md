# Prepare the Environment
[中文文档](./install_guide-zh.md)

This guide is about building a python environment for Real3D-Portrait with Conda.

The following installation process is verified in A100/V100 + CUDA11.7.


# 1. Install CUDA
 We recommend to install CUDA `11.7` (which is verified in various types of GPUs), but other CUDA versions (such as `10.2`, `12.x`) may also work well. 

# 2. Install Python Packages
```
cd <Real3DPortraitRoot>
source <CondaRoot>/bin/activate
conda create -n real3dportrait python=3.9
conda activate real3dportrait
conda install conda-forge::ffmpeg # ffmpeg with libx264 codec to turn images to video

### We recommend cuda11.7.
conda install  librosa pytorch3d pytorch torchvision torchaudio cudatoolkit=11.7 -c pytorch

# MMCV for some network structure
pip install cython
pip install openmim==0.3.9
mim install mmcv==2.1.0 # use mim to speed up installation for mmcv

# other dependencies
pip install -r docs/prepare_env/requirements.txt -v

If you encounter the following error, please try to install the dependencies with the following command:
pip install -r docs/prepare_env/requirements.txt -v --use-deprecated=legacy-resolver

> ERROR: pip's dependency resolver does not currently take into account all the packages
> that are installed. This behaviour is the source of the following dependency conflicts.
> openxlab 0.0.34 requires setuptools~=60.2.0, but you have setuptools 69.1.1 which is incompatible.

```
