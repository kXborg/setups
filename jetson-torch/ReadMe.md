## Steps to Install Torch in Jeson Orin Nano

1. Check Installations
```
apt list --installed | grep nvidia-jetpack

dpkg-query --show nvidia-l4t-core

sudo bash -c 'echo "deb https://repo.download.nvidia.com/jetson/common r34.1 main" >> /etc/apt/sources.list.d/nvidia-l4t-apt-source.list'

sudo bash -c 'echo "deb https://repo.download.nvidia.com/jetson/t234 r34.1 main" >> /etc/apt/sources.list.d/nvidia-l4t-apt-source.list'

sudo apt update
sudo apt dist-upgrade

sudo apt install nvidia-jetpack
apt list --installed | grep nvidia-jetpack
apt list --installed | grep cuda-toolkit
apt list --installed | grep cudnn

sudo apt update
sudo apt upgrade -y 

sudo apt install python3-pip -y
sudo -H pip3 install -U jetson-stats

jtop

sudo systemctl restart jtop.service

sudo reboot now

jtop 

dpkg-query --show nvidia-l4t-core

sudo apt-get install -y  python3-pip libopenblas-dev
export CUDA_VERSION=12.6

wget https://developer.download.nvidia.com/compute/cusparselt/0.8.1/local_installers/cusparselt-local-tegra-repo-ubuntu2204-0.8.1_0.8.1-1_arm64.deb

sudo dpkg -i cusparselt-local-tegra-repo-ubuntu2204-0.8.1_0.8.1-1_arm64.deb
sudo cp /var/cusparselt-local-tegra-repo-ubuntu2204-0.8.1/cusparselt-local-tegra-C4CC87E1-keyring.gpg /usr/share/keyrings/

sudo cp /var/cusparselt-local-tegra-repo-ubuntu2204-0.8.1/cusparselt-local-tegra-C4CC87E1-keyring.gpg /usr/share/keyrings/

sudo apt update
sudo apt -y install cusparselt-cuda-12

wget https://pypi.jetson-ai-lab.io/jp6/cu126/+f/590/92ab729aee2b8/torch-2.8.0-cp310-cp310-linux_aarch64.whl#sha256=59092ab729aee2b8937d80cc1b35d1128275bd02a7e1bc911e7efa375bd97226 -O torch-2.8.0-cp310-cp310-linux_aarch64.whl

wget https://pypi.jetson-ai-lab.io/jp6/cu126/+f/de1/5388b8f70e4e1/torchaudio-2.8.0-cp310-cp310-linux_aarch64.whl#sha256=de15388b8f70e4e17a05b23a4ae1f55a288c91449371bb8aeeb69184d40be17f -O torchaudio-2.8.0-cp310-cp310-linux_aarch64.whl

wget https://pypi.jetson-ai-lab.io/jp6/cu126/+f/1c0/3de08a69e9554/torchvision-0.23.0-cp310-cp310-linux_aarch64.whl#sha256=1c03de08a69e95542024477e0cde95fab3436804917133d3f00e67629d3fe902 -O torchvision-0.23.0-cp310-cp310-linux_aarch64.whl

export TORCH_INSTALL=~/Downloads/torch-2.8.0-cp310-cp310-linux_aarch64.whl

python3 -m pip install --no-cache $TORCH_INSTALL
python3 -m pip install numpy
python3 -m pip install torchvision-0.23.0-cp310-cp310-linux_aarch64.whl
python3 -m pip install torchaudio-2.8.0-cp310-cp310-linux_aarch64.whl

echo $LD_LIBRARY_PATH
mkdir -p tmp_cudss && cd tmp_cudss

mkdir -p tmp_cudss && cd tmp_cudss
CUSPARSE_SOLVER_NAME="libcudss-linux-sbsa-0.6.0.5_cuda12-archive"

 curl -L -O https://developer.download.nvidia.com/compute/cudss/redist/libcudss/linux-sbsa/${CUSPARSE_SOLVER_NAME}.tar.xz

 tar xf ${CUSPARSE_SOLVER_NAME}.tar.xz

sudo cp -a ${CUSPARSE_SOLVER_NAME}/include/* /usr/local/cuda/include/
sudo cp -a ${CUSPARSE_SOLVER_NAME}/lib/* /usr/local/cuda/lib64/
cd ..                                                                                             
rm -rf tmp_cudss                                                                                         
sudo ldconfig
ls /usr/local/cuda/lib64 | grep cudss

pip install transformers accelerate huggingface_hub

pip install pyvips
pip install einops timm

```