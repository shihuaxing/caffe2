## Building Caffe2

This guide builds from source. For alternatives, refer to https://caffe2.ai/docs/getting-started.html

Get latest source from GitHub.

    git clone --recursive https://github.com/caffe2/caffe2.git
    cd caffe2

#### MacOS X

    brew install openblas glog gtest automake protobuf leveled lmdb
    mkdir build && cd build
    cmake .. -DBLAS=OpenBLAS -DUSE_OPENCV=off
    make

#### Ubuntu

    sudo apt-get install libprotobuf-dev protobuf-compiler libatlas-base-dev libgoogle-glog-dev libgtest-dev liblmdb-dev libleveldb-dev libsnappy-dev python-dev python-pip libiomp-dev libopencv-dev libpthread-stubs0-dev cmake
    sudo pip install numpy
    wget http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1404/x86_64/cuda-repo-ubuntu1404_8.0.44-1_amd64.deb
    sudo dpkg -i cuda-repo-ubuntu1404_8.0.44-1_amd64.deb
    sudo apt-get update
    sudo apt-get install cuda
    sudo apt-get install git

    CUDNN_URL="http://developer.download.nvidia.com/compute/redist/cudnn/v5.1/cudnn-8.0-linux-x64-v5.1.tgz" &&
    curl -fsSL ${CUDNN_URL} -O &&
    sudo tar -xzf cudnn-8.0-linux-x64-v5.1.tgz -C /usr/local &&
    rm cudnn-8.0-linux-x64-v5.1.tgz &&
    sudo ldconfig

    mkdir build && cd build
    cmake ..
    make

## Python support

To use Caffe2 in Python, you need two libraries, future and six.

    pip install future six

To run the tutorials you'll need jupyter (formerly ipython) notebooks and matplotlib, which can be installed on MacOS X with

    brew install matplotlib --with-python3
    pip install jupyter
