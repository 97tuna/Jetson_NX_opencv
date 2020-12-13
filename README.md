# Jetson_NX_opencv

At Jetson NX, the opencv installation is very difficult, so we recommend you install it using the following method.

## Install OpenCV in Jetson NX

### Remove OpenCV4.1 first
```
sudo sudo apt-get purge *libopencv*
```

### Install requirement
```
sudo apt-get update
sudo apt-get install -y build-essential cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
sudo apt-get install -y libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev
sudo apt-get install -y python2.7-dev python3.6-dev python-dev python-numpy python3-numpy
sudo apt-get install -y libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev
sudo apt-get install -y libv4l-dev v4l-utils qv4l2 v4l2ucp
sudo apt-get install -y curl unzip zip
sudo apt-get update
```

### Download opencv-4.4.0
```
sudo curl -L https://github.com/opencv/opencv/archive/4.4.0.zip -o opencv-4.4.0.zip
sudo curl -L https://github.com/opencv/opencv_contrib/archive/4.4.0.zip -o opencv_contrib-4.4.0.zip
sudo unzip opencv-4.4.0.zip 
sudo unzip opencv_contrib-4.4.0.zip 
cd opencv-4.4.0/
```

### Building
```
sudo mkdir release
cd release/
sudo cmake -D WITH_CUDA=ON -D ENABLE_PRECOMPILED_HEADERS=OFF  -D CUDA_ARCH_BIN="7.2" -D CUDA_ARCH_PTX="" -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib-4.4.0/modules -D WITH_GSTREAMER=ON -D WITH_LIBV4L=ON -D BUILD_opencv_python2=ON -D BUILD_opencv_python3=ON -D BUILD_TESTS=OFF -D BUILD_PERF_TESTS=OFF -D BUILD_EXAMPLES=OFF -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local ..
sudo make -j6
sudo make install
```

### Install opencv-4.4.0 successfully
