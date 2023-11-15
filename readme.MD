YOLO V7 CUDA LIBTORCH

Real time object detection with deployment of YOLOv7 through LibTorch C++ API

Environment
 * Ubuntu 20.04
 * OpenCV 4.2.0
 * Libtorch 1.13 CUDA 11.6
 * Cmake 3.10.2
 * CuDNN 8.9.6.50

Getting started

Install Cuda Toolkit 11.4 (**REQUIRED)

1. Install CuDNN (Tar File Installation)

* Download CuDNN
```
    https://developer.nvidia.com/downloads/compute/cudnn/secure/8.9.6/local_installers/11.x/cudnn-linux-x86_64-8.9.6.50_cuda11-archive.tar.xz
```
* Unzip tar file

```
    tar -xvf cudnn-linux-x86_64-8.9.6.50_cuda11-archive.tar.xz
```

* Copy the following files into the CUDA toolkit directory

```
    sudo cp cudnn-linux-x86_64-8.9.6.50_cuda11-archive/include/cudnn*.h /usr/local/cuda-11.4/include 
    sudo cp -P cudnn-linux-x86_64-8.9.6.50_cuda11-archive/lib/libcudnn* /usr/local/cuda-11.4/lib64
    sudo chmod a+r /usr/local/cuda-11.4/include/cudnn*.h /usr/local/cuda-11.4/lib64/libcudnn*
```

2. Install Libtorch (CUDA)

* Download Libtorch
```
    wget https://download.pytorch.org/libtorch/cu116/libtorch-cxx11-abi-static-with-deps-1.13.1%2Bcu116.zip
```

* Unzip Libtorch here

```
    unzip libtorch-cxx11-abi-static-with-deps-1.13.1+cu116.zip
```

=> "libtorch" folder here

3. Export YOLOV7 model

use export.py from (https://github.com/WongKinYiu/yolov7#export) for export pretrained

4. Change pretrained in .cpp file

Change pretrained path in src/[YOLOv7LibTorch.cpp](src%2FYOLOv7LibTorch.cpp) line 81

5. Build project

Please check nvcc
```
nvcc --version
```

if NVCC is not found

```
export CUDA_HOME=/usr/local/cuda-11.4
export PATH=/usr/local/cuda-11.4/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda-11.4/lib64:$LD_LIBRARY_PATH
```

Build this project
```
    mkdir build
    cd build
    cmake ..
    make
```

6. Run this project

```
cd bin
./YOLOv7LibTorch
```
