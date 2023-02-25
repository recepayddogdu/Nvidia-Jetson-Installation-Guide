# Dlib Installation

sudo apt-get install libpng-dev

sudo apt-get install python3-pil

sudo apt-get install python3-dev

pip3 install --upgrade --no-cache-dir dlib

---

# For Jetson

sudo apt-get install  python3-pil

[Install dlib(from source, gpu) on Jetson NX did not work correctly](https://stackoverflow.com/questions/69837794/install-dlibfrom-source-gpu-on-jetson-nx-did-not-work-correctly)

> My environment: Xavier NX + JetPack 4.6
> 
> 
> I solved this issue following the help here: [https://forums.developer.nvidia.com/t/simple-accelerated-face-recognition/142679/19](https://forums.developer.nvidia.com/t/simple-accelerated-face-recognition/142679/19)
> 
> **Most importantly, make sure you use dlib19.21, neither dlib19.23 nor dlib 19.17.**
> 

[Simple accelerated face recognition](https://forums.developer.nvidia.com/t/simple-accelerated-face-recognition/142679/19)

Hi,

The fix is adding the cuDNNv8 new API support.And it is available in the newest *dlib-19.21* release in Aug 8.

So you can build it from source directly:

### Install dependencies

```
$ sudo apt-get install python3-pip
$ sudo apt-get install libjpeg-dev

```

### Build *dlib* from source

[dlib-19.21.tar.bz2](Dlib%20Installation%209d1214a0cba5484e8cb9c2037995142d/dlib-19.21.tar.bz2)

```
$ wget http://dlib.net/files/dlib-19.21.tar.bz2
$ tar jxvf dlib-19.21.tar.bz2
$ cd dlib-19.21/
$ mkdir build
$ cd build/
$ cmake ..
$ cmake --build .
$ cd ../
$ sudo python3 setup.py install
$ sudo pip3 install face_recognition

```

### Testing

Please create *Images* folder and store some testing images in the folder.

*test.py*

```
import cv2
import os
import numpy as np
import dlib

face_locations = []
face_encodings = []

### Path where images are present for testingimagefolderpath = "Images/"

### Model for face detectionface_detector = dlib.get_frontal_face_detector()

for image in os.listdir(imagefolderpath):
    image = cv2.imread(os.path.join(imagefolderpath,image),1)

    t = time.time()
    faces = face_detector(image,0)
    for face in faces:
        x,y,w,h = face.left(),face.top(),face.right(),face.bottom()
        face_locations.append((x,y,h,w))
    face_encodings = face_recognition.face_encodings(image, known_face_locations = face_locations, num_jitters = 1)

    for (left, top, bottom, right) in face_locations:
        cv2.rectangle(image, (left,top), (right, bottom), (0, 0, 255), 2)
        cv2.imshow('Image', image)
        cv2.waitKey(0)
        cv2.destroyAllWindows()

```

```
python3 test.py

```

### You should be able to see CUDA and cuDNN are both enabled in the *dlib-19.21*.

```
...
-- Found CUDA: /usr/local/cuda (found suitable version "10.2", minimum required is "7.5")-- Looking for cuDNN install...-- Found cuDNN: /usr/lib/aarch64-linux-gnu/libcudnn.so-- Building a CUDA test project to see if your compiler is compatible with CUDA...-- Building a cuDNN test project to check if you have the right version of cuDNN installed...-- Enabling CUDA support for dlib.  DLIB WILL USE CUDA-- C++11 activated.-- Configuring done-- Generating done-- Build files have been written to: /home/nvidia/dlib-19.21/build
```

Thanks.