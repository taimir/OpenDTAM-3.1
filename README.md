OpenDTAM for Opencv 3.1
========

An open source implementation of DTAM

Based on Newcombe, Richard A., Steven J. Lovegrove, and Andrew J. Davison's "DTAM: Dense tracking and mapping in real-time."

This project depends on qtbase5-dev, [OpenCV 3](https://github.com/Itseez/opencv "OpenCV") and [Cuda](https://developer.nvidia.com/cuda-downloads "Cuda").

## Build Instructions on Ubuntu 16.04

Tested in this environment

* Ubuntu 16.04 x64
* GCC 5.4.0
* Boost 1.5.8
* OpenCV 3.1
* Cuda Toolkit 7.5

### Install dependencies

#### qtbase5-dev

```bash
sudo apt-add-repository ppa:ubuntu-sdk-team/ppa
sudo apt-get update
sudo apt-get install qtbase5-dev
```

#### boost

```bash
sudo apt-get install libboost-system-dev libboost-thread-dev
```

#### Cuda

Version 7.5 was used. 

You can use the pre-built downloads from [NVIDIA](https://developer.nvidia.com/cuda-downloads "Cuda"), or you can follow this guide:

[Cuda Installation Tutorial](https://www.pugetsystems.com/labs/hpc/NVIDIA-CUDA-with-Ubuntu-16-04-beta-on-a-laptop-if-you-just-cannot-wait-775/ "Cuda Installation Tutorial")

#### OpenCV 3

These lines were mostly stitched together from the [caffee installation guide](https://github.com/BVLC/caffe/wiki/Ubuntu-16.04-or-15.10-OpenCV-3.1-Installation-Guide "caffe installation guide")

```bash
# Execute first command from directory you would like to clone OpenCV
git clone https://github.com/opencv/opencv.git
cd opencv
# make sure to use version 3.1.0
git checkout tags/3.1.0
mkdir build
cd build
cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D WITH_TBB=ON -D WITH_V4L=ON -D WITH_QT=ON -D WITH_OPENGL=ON -DCUDA_NVCC_FLAGS="-D_FORCE_INLINES" ..
make -j4
sudo make install
```

### Build OpenDTAM
```bash
cd OpenDTAM
mkdir build
cd build
cmake ../Cpp
make -j4
````

### Run OpenDTAM
For the following command, replace `$TRAJECTORY_30_SECONDS` with the path to the directory of the same name.
```bash
./a.out $TRAJECTORY_30_SECONDS
```
Assuming you are executing this command from the build folder, as shown above, enter the following:
```bash
./a.out ../Trajectory_30_seconds
```
