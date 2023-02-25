# How to Apply Distro Upgrade (apt upgrade) on Jetson Modules

In this blog post, we will prevent the L4T packages’ upgrading on “apt upgrade” or “apt-get upgrade” commands. First, we will hold the “nvidia-l4t-*” packages to upgrade. Then, we will upgrade our all packages without them.

## **Holding the L4T Packages**

Open a terminal and type this command below:

`sudo apt-mark hold 'nvidia-l4t-*'`

![https://ucarecdn.com/4c275433-b5a5-428c-a119-af30f4fd6da0/-/format/auto/-/preview/1024x1024/-/quality/lighter/1.png](https://ucarecdn.com/4c275433-b5a5-428c-a119-af30f4fd6da0/-/format/auto/-/preview/1024x1024/-/quality/lighter/1.png)

As you can see that, all “nvidia-l4t-*” packages set on hold.

Now, let’s update all packages with APT.

## **Upgrading All Packages Without L4T**

To check the updates on all packages, type this command on terminal:

`sudo apt-get update`

![https://ucarecdn.com/f00e959a-6132-4a5e-9231-5cf4a852c38f/-/format/auto/-/preview/1024x1024/-/quality/lighter/2.png](https://ucarecdn.com/f00e959a-6132-4a5e-9231-5cf4a852c38f/-/format/auto/-/preview/1024x1024/-/quality/lighter/2.png)

Then, you can try to upgrade them:

`sudo apt-get upgrade`

![https://ucarecdn.com/0de20481-f1f4-4d1a-ad8b-b0efbae9e57d/-/format/auto/-/preview/1024x1024/-/quality/lighter/3.png](https://ucarecdn.com/0de20481-f1f4-4d1a-ad8b-b0efbae9e57d/-/format/auto/-/preview/1024x1024/-/quality/lighter/3.png)

At the beginning of this command, you can see all hold packages will keep back.

At this point, press “y” to accept installing packages on the Jetson module.

![https://ucarecdn.com/364cd7b7-5a5a-4688-bf6f-918c4d4d2283/-/format/auto/-/preview/1024x1024/-/quality/lighter/4.png](https://ucarecdn.com/364cd7b7-5a5a-4688-bf6f-918c4d4d2283/-/format/auto/-/preview/1024x1024/-/quality/lighter/4.png)

A few minutes later... (it depends on network speed)

![https://ucarecdn.com/dc1d34ed-5fda-431a-aa64-2257aadb3cb1/-/format/auto/-/preview/1024x1024/-/quality/lighter/5.png](https://ucarecdn.com/dc1d34ed-5fda-431a-aa64-2257aadb3cb1/-/format/auto/-/preview/1024x1024/-/quality/lighter/5.png)

At the end of the upgrading step, you can check it again.

![https://ucarecdn.com/c8935d44-dc53-49b2-a6f1-29afaa8dbbff/-/format/auto/-/preview/1024x1024/-/quality/lighter/6.png](https://ucarecdn.com/c8935d44-dc53-49b2-a6f1-29afaa8dbbff/-/format/auto/-/preview/1024x1024/-/quality/lighter/6.png)

As you can see that, the holding command works.