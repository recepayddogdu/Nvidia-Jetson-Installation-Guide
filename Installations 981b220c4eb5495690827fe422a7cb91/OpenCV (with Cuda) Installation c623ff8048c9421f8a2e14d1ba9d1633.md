# OpenCV (with Cuda) Installation

[opencv-4-5-2 - Google Drive](https://drive.google.com/drive/folders/1e_1BUicwW87hHQG1WUWmI-OH-lH7uhY-)

First of all install update and upgrade your system:

```
    $ sudo apt update
    $ sudo apt upgrade
```

Then, install required libraries:

- Generic tools:
    
    ```
      $ sudo apt install build-essential cmake pkg-config unzip yasm git checkinstall
    ```
    
- Image I/O libs
    
    ```
    $ sudo apt install libjpeg-dev libpng-dev libtiff-dev
    
    ```
    
- Video/Audio Libs - FFMPEG, GSTREAMER, x264 and so on.
    
    ```
    $ sudo apt install libavcodec-dev libavformat-dev libswscale-dev libavresample-dev
    $ sudo apt install libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev
    $ sudo apt install libxvidcore-dev x264 libx264-dev libfaac-dev libmp3lame-dev libtheora-dev
    $ sudo apt install libfaac-dev libmp3lame-dev libvorbis-dev
    
    ```
    
- **(Optional)** OpenCore - Adaptive Multi Rate Narrow Band (AMRNB) and Wide Band (AMRWB) speech codec
    
    ```
    $ sudo apt install libopencore-amrnb-dev libopencore-amrwb-dev
    
    ```
    
- Cameras programming interface libs
    
    ```
    $ sudo apt-get install libdc1394-22 libdc1394-22-dev libxine2-dev libv4l-dev v4l-utils
    $ cd /usr/include/linux
    $ sudo ln -s -f ../libv4l1-videodev.h videodev.h
    $ cd ~
    ```
    
- GTK lib for the graphical user functionalites coming from OpenCV highghui module
    
    ```
    $ sudo apt-get install libgtk-3-dev
    ```
    
- Python libraries for python3:
    
    ```
    $ sudo apt-get install python3-dev python3-pip
    $ sudo -H pip3 install -U pip numpy
    $ sudo apt install python3-testresources
    ```
    
- Parallelism library C++ for CPU
    
    ```
    $ sudo apt-get install libtbb-dev
    ```
    
- Optimization libraries for OpenCV
    
    ```
    $ sudo apt-get install libatlas-base-dev gfortran
    ```
    
- Optional libraries:
    
    ```
    $ sudo apt-get install libprotobuf-dev protobuf-compiler
    $ sudo apt-get install libgoogle-glog-dev libgflags-dev
    $ sudo apt-get install libgphoto2-dev libeigen3-dev libhdf5-dev doxygen
    ```
    

We will now proceed with the installation (see the Qt flag that is disabled to do not have conflicts with Qt5.0).

```python
$ cd ~/Downloads
$ wget -O opencv.zip https://github.com/opencv/opencv/archive/refs/tags/4.5.2.zip
$ wget -O opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/refs/tags/4.5.2.zip
$ unzip opencv.zip
$ unzip opencv_contrib.zip
```

```python
$ echo "Create a virtual environtment for the python binding module (OPTIONAL)"
$ sudo pip install virtualenv virtualenvwrapper
$ sudo rm -rf ~/.cache/pip
$ echo "Edit ~/.bashrc"
$ export WORKON_HOME=$HOME/.virtualenvs
$ export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3
$ source /usr/local/bin/virtualenvwrapper.sh
$ mkvirtualenv cv -p python3
$ pip install numpy
```

```python
$ echo "Procced with the installation"
$ cd opencv-4.5.2
$ mkdir build
$ cd build
```

```
cmake \
-D CMAKE_BUILD_TYPE=RELEASE \
-D CMAKE_INSTALL_PREFIX=/usr/local \
-D OPENCV_EXTRA_MODULES_PATH=/home/nvidia/Tools/opencv-4-5-2/opencv_contrib-4.5.2/modules \
-D WITH_CUDA=ON \
-D WITH_CUBLAS=ON \
-D WITH_CUDNN=ON \
-D CUDA_ARCH_BIN=7.2 \
-D CUDA_ARCH_PTX="" \
-D CUDA_FAST_MATH=ON \
-D ENABLE_FAST_MATH=ON \	
-D OPENCV_DNN_CUDA=ON \
-D ENABLE_NEON=OFF \
-D BUILD_TIFF=ON \
-D WITH_QT=OFF \
-D WITH_TBB=ON \
-D BUILD_TBB=ON \
-D WITH_FFMPEG=ON \
-D OPENCV_ENABLE_NONFREE=ON \
-D OPENCV_PYTHON3_INSTALL_PATH=~/.virtualenvs/cv/lib/python3.8/site-packages \
-D PYTHON_EXECUTABLE=~/.virtualenvs/cv/bin/python \
-D BUILD_TESTS=OFF \
-D BUILD_PERF_TESTS=OFF \
-D OPENCV_GENERATE_PKGCONFIG=ON \
-D BUILD_EXAMPLES=OFF ..
```

```python
#-D WITH_OPENMP=ON  
# deneysel, daha fazla kaynak tuketerek daha hizli islem yapilmasi saglanabilir.
```

I've included below the output of my [configuration](https://gist.github.com/raulqf/f42c718a658cddc16f9df07ecc627be7#configuration-information).

If it is fine proceed with the compilation (Use nproc to know the number of cpu cores):

```
$ nproc
$ make -j6
$ sudo make install
```

**********************(Optional)********************** If you want to have available opencv python bindings in the system environment you should copy the created folder during the installation of OpenCV (* -D OPENCV_PYTHON3_INSTALL_PATH=~/.virtualenvs/cv/lib/python3.8/site-packages *) into the *dist-packages* folder of the target python interpreter:

```
$ sudo cp -r ~/.virtualenvs/cv/lib/python3.8/site-packages/cv2 /usr/local/lib/python3.8/dist-packages

$ echo "Modify config-3.8.py to point to the target directory"
$ sudo nano /usr/local/lib/python3.8/dist-packages/cv2/config-3.8.py

```
    PYTHON_EXTENSIONS_PATHS = [
    os.path.join('/usr/local/lib/python3.8/dist-packages/cv2', 'python-3.8')
    ] + PYTHON_EXTENSIONS_PATHS
```
```

---

[How to install OpenCV 4.5 with CUDA 11.2 in Ubuntu 20.04](https://gist.github.com/raulqf/f42c718a658cddc16f9df07ecc627be7)

---

[Other Sources](OpenCV%20(with%20Cuda)%20Installation%20c623ff8048c9421f8a2e14d1ba9d1633/Other%20Sources%20784749551b504211a76bdd9851e7ef77.md)