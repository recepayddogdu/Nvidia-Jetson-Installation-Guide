# MediaPipe Installation

> **************************************************************************************************************pip ile kurulduğunda virtual environment’e değil global environment’e kurulum yapılıyor. Aşağıdaki blog’da da virtual environment’e değil global environment’e kurulum yapılmış.**************************************************************************************************************
> 
 
> 1. How to Download & Build MediaPipe?
> 
> 2. How to Install MediaPipe?
> 

In this blog-post, we will download & build MediaPipe on NVIDIA Jetson Xavier NX. First, we will download the source files from GitHub. Then, we will install the required packages. Finally, we will build & test it using a test file.

## **How to Download & Build MediaPipe?**

Follow the instruction to setup Bazel from **[here](How%20to%20Install%20Bazel%206961195e4c6a48128cef5a2c771c1234.md)**  ([Alternative](https://www.forecr.io/blogs/installation/how-to-install-bazel)).

Then, clone the MediaPipe repository with the command below.

`git clone https://github.com/google/mediapipe.git`

![https://ucarecdn.com/7b1e249e-c7c3-4946-9b91-48e787e2cf47/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2008-50-00.png](https://ucarecdn.com/7b1e249e-c7c3-4946-9b91-48e787e2cf47/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2008-50-00.png)

`sudo apt-get update`

![https://ucarecdn.com/3cbd6954-aeac-4751-8b60-4753bd680084/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2008-55-50.png](https://ucarecdn.com/3cbd6954-aeac-4751-8b60-4753bd680084/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2008-55-50.png)

Install python3-dev using the command:

`sudo apt install -y python3-dev`

![https://ucarecdn.com/bee82c76-81e2-4364-a84b-c8dc095a11ae/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2009-56-44.png](https://ucarecdn.com/bee82c76-81e2-4364-a84b-c8dc095a11ae/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2009-56-44.png)

Install cmake using the command:

`sudo apt install -y cmake`

![https://ucarecdn.com/1651c64f-7f6c-4635-a7bd-23eb361218de/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2009-58-09.png](https://ucarecdn.com/1651c64f-7f6c-4635-a7bd-23eb361218de/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2009-58-09.png)

Install protobuf-compiler using the command:

`sudo apt install -y protobuf-compiler`

![https://ucarecdn.com/4f1309d0-81a2-42f3-8b0c-1e2d432e1fc1/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2010-00-21.png](https://ucarecdn.com/4f1309d0-81a2-42f3-8b0c-1e2d432e1fc1/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2010-00-21.png)

Install pip using the command:

`sudo apt install pip`

![https://ucarecdn.com/f26581da-0bbc-40eb-8660-50641128c215/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2010-56-57.png](https://ucarecdn.com/f26581da-0bbc-40eb-8660-50641128c215/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2010-56-57.png)

Install cython using the command:

`python3 -m pip install cython`

![https://ucarecdn.com/8d7f360f-a036-4634-b23b-b4ffb782355f/-/format/auto/-/preview/1024x1024/-/quality/lighter/1.png](https://ucarecdn.com/8d7f360f-a036-4634-b23b-b4ffb782355f/-/format/auto/-/preview/1024x1024/-/quality/lighter/1.png)

Install dlib using the command:

`python3 -m pip install dlib`

![https://ucarecdn.com/7260124b-b76b-450a-b8fc-1065585a8181/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2012-35-24.png](https://ucarecdn.com/7260124b-b76b-450a-b8fc-1065585a8181/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2012-35-24.png)

Install imutils using the command:

`python3 -m pip install imutils`

![https://ucarecdn.com/c12f6a62-b51e-4b85-a8a8-a1371b62b580/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2012-36-52.png](https://ucarecdn.com/c12f6a62-b51e-4b85-a8a8-a1371b62b580/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2012-36-52.png)

Install numpy using the command:

`python3 -m pip install numpy==1.22.3`

![https://ucarecdn.com/c70e0f27-d6e8-4f7f-8aee-d7b4c54f8342/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2012-44-22.png](https://ucarecdn.com/c70e0f27-d6e8-4f7f-8aee-d7b4c54f8342/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2012-44-22.png)

Then, modify mediapipe/setup.py like the following:

Delete selected line and add given line:

“self._protoc, '-I.', '-I/usr/local/include', '--python_out=' + os.path.abspath(self.build_lib), source”

![https://ucarecdn.com/fe4897c0-3b32-4463-a1cb-14e70686c1d6/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2010-06-06.png](https://ucarecdn.com/fe4897c0-3b32-4463-a1cb-14e70686c1d6/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2010-06-06.png)

![https://ucarecdn.com/438790de-9c74-411d-94c5-3c2a4f6523b7/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2010-16-04.png](https://ucarecdn.com/438790de-9c74-411d-94c5-3c2a4f6523b7/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2010-16-04.png)

After that save the file and close it.

Go to the MediaPipe directory. Remove unnecessary OpenCV modules and linker flags.

`sed -i -e "/\"imgcodecs\"/d;/\"calib3d\"/d;/\"features2d\"/d;/\"highgui\"/d;/\"video\"/d;/\"videoio\"/d" third_party/BUILDsed -i -e "/-ljpeg/d;/-lpng/d;/-ltiff/d;/-lImath/d;/-lIlmImf/d;/-lHalf/d;/-lIex/d;/-lIlmThread/d;/-lrt/d;/-ldc1394/d;/-lavcodec/d;/-lavformat/d;/-lavutil/d;/-lswscale/d;/-lavresample/d" third_party/BUILD`

![https://ucarecdn.com/0787dd8e-52ae-43a1-a3e9-8e99e48a73d7/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2010-31-07.png](https://ucarecdn.com/0787dd8e-52ae-43a1-a3e9-8e99e48a73d7/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2010-31-07.png)

Add given lines to cmake_external in third_party/BUILD file.

"ENABLE_NEON": "OFF",

"WITH_TENGINE": "OFF",

![https://ucarecdn.com/0b1e6660-2ebb-4ffe-9735-f896e4929da3/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2010-36-21.png](https://ucarecdn.com/0b1e6660-2ebb-4ffe-9735-f896e4929da3/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2010-36-21.png)

Build MediaPipe using the command:

`python3 setup.py gen_protos && python3 setup.py bdist_wheel`

![https://ucarecdn.com/948e393c-3ebf-4abe-89fb-618287a2c965/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2010-39-57.png](https://ucarecdn.com/948e393c-3ebf-4abe-89fb-618287a2c965/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2010-39-57.png)

![https://ucarecdn.com/63ea4bec-a0e1-45ad-9e89-0443abbc7f92/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2011-09-28.png](https://ucarecdn.com/63ea4bec-a0e1-45ad-9e89-0443abbc7f92/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2011-09-28.png)

![https://ucarecdn.com/3b81a6a6-85dc-4662-8550-9a22ac8e0bee/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2012-11-40.png](https://ucarecdn.com/3b81a6a6-85dc-4662-8550-9a22ac8e0bee/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2012-11-40.png)

## **How to Install MediaPipe?**

Install MediaPipe using built package (The username is "nvidia" on our Jetson).

`python3 -m pip install /home/nvidia/mediapipe/dist/mediapipe-dev-cp38-cp38-linux_aarch64.whl`

![https://ucarecdn.com/0ef1abac-2fb1-479e-9f2a-5cdb8caf2a82/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2012-53-54.png](https://ucarecdn.com/0ef1abac-2fb1-479e-9f2a-5cdb8caf2a82/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2012-53-54.png)

Let's test MediaPipe with the test files under Python directory (The username is "nvidia" on our Jetson).

`python3 /home/nvidia/mediapipe/mediapipe/python/image_test.py`

![https://ucarecdn.com/cf03268d-3f00-493e-9316-244577ba5495/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2012-55-47.png](https://ucarecdn.com/cf03268d-3f00-493e-9316-244577ba5495/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202022-09-27%2012-55-47.png)

### Source

[How to Download &amp; Build MediaPipe on NVIDIA Jetson Xavier NX?](https://www.forecr.io/blogs/ai-algorithms/how-to-download-build-mediapipe-on-nvidia-jetson-xavier-nx)

---

---

---

---

[Other Sources](MediaPipe%20Installation%206045ee0efb09499a82608ad5ae3dc695/Other%20Sources%20aa7072283f7a4924b62ca764359d3129.md)