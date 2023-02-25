# How to Clear The External Storage on Jetson Modules

In this guide we will change the Filesystem Root storage from external to internal storage (eMMC). Then, we will format the external storage.

Sometimes we need to re-flash (or upgrade) our Jetson modules. Using an external storage as Filesystem Root cause a few problems after doing it. We have to follow these steps below to avoid these problems.

This guide prepared for SSD mounted system but you can follow the same steps in your SD card mounted system.

*Attention:* If the Jetson module does not use its external storage as Filesystem Root, you don’t need to erase it.

## **Changing the Filesystem Root**

If you have follow one of blog-posts below to transferring the Filesystem Root to your external storage, you can just modify the boot/extlinux/extlinux.conf files located on both storages.

• [https://www.forecr.io/blogs/bsp-development/change-root-file-system-to-sd-card-directly](https://www.forecr.io/blogs/bsp-development/change-root-file-system-to-sd-card-directly)

• [https://www.forecr.io/blogs/bsp-development/change-root-file-system-to-m-2-ssd-directly](https://www.forecr.io/blogs/bsp-development/change-root-file-system-to-m-2-ssd-directly)

First, open a terminal on your Jetson. Then, type "df -h".

As you can see that our SSD connected on "/" (as Filesystem Root). If you are using an SD card, you should see “/dev/mmcblk1p1” device mounted as root (/).

![https://ucarecdn.com/02283014-404b-4f95-b6fd-f7aaf7c3f65c/-/format/auto/-/preview/1024x1024/-/quality/lighter/1.png](https://ucarecdn.com/02283014-404b-4f95-b6fd-f7aaf7c3f65c/-/format/auto/-/preview/1024x1024/-/quality/lighter/1.png)

At this point we need to change two extlinux.conf files which located on boot/extlinux folders both eMMC & SSD.

We started to modify the file at the SSD. Type this command to open it:

`sudo gedit /boot/extlinux/extlinux.conf`

![https://ucarecdn.com/ed0ca0d8-048c-4567-b9bf-f42b1964f017/-/format/auto/-/preview/1024x1024/-/quality/lighter/2.png](https://ucarecdn.com/ed0ca0d8-048c-4567-b9bf-f42b1964f017/-/format/auto/-/preview/1024x1024/-/quality/lighter/2.png)

![https://ucarecdn.com/39c7c1b8-53fb-46be-8eaa-d27e4bf30a13/-/format/auto/-/preview/1024x1024/-/quality/lighter/3.png](https://ucarecdn.com/39c7c1b8-53fb-46be-8eaa-d27e4bf30a13/-/format/auto/-/preview/1024x1024/-/quality/lighter/3.png)

As you can see that, the "root" parameter set as "/dev/nvme0n1p1". (If you are using an SD card, you should see “/dev/mmcblk1p1”). You need to change it as "/dev/mmcblk0p1".

![https://ucarecdn.com/628df8a1-1821-4e69-bd81-a181e14cf120/-/format/auto/-/preview/1024x1024/-/quality/lighter/4.png](https://ucarecdn.com/628df8a1-1821-4e69-bd81-a181e14cf120/-/format/auto/-/preview/1024x1024/-/quality/lighter/4.png)

Then, save it and close.

Open the File Manager and open your internal storage (eMMC).

![https://ucarecdn.com/056a73cc-f0bb-45f1-af98-2f1bf9b350fa/-/format/auto/-/preview/1024x1024/-/quality/lighter/5.png](https://ucarecdn.com/056a73cc-f0bb-45f1-af98-2f1bf9b350fa/-/format/auto/-/preview/1024x1024/-/quality/lighter/5.png)

Open the “boot/extlinux” folder & open a terminal from here.

![https://ucarecdn.com/7fb3773c-c3d0-4e57-ac25-7327fe3d61e4/-/format/auto/-/preview/1024x1024/-/quality/lighter/6.png](https://ucarecdn.com/7fb3773c-c3d0-4e57-ac25-7327fe3d61e4/-/format/auto/-/preview/1024x1024/-/quality/lighter/6.png)

Type this command below to modify the second extlinux.conf file:

`sudo gedit extlinux.conf`

![https://ucarecdn.com/11a4c92b-71bd-42bb-8270-cfea12a2d14c/-/format/auto/-/preview/1024x1024/-/quality/lighter/7.png](https://ucarecdn.com/11a4c92b-71bd-42bb-8270-cfea12a2d14c/-/format/auto/-/preview/1024x1024/-/quality/lighter/7.png)

![https://ucarecdn.com/649993b8-04dd-4885-ae16-ec6178094c94/-/format/auto/-/preview/1024x1024/-/quality/lighter/8.png](https://ucarecdn.com/649993b8-04dd-4885-ae16-ec6178094c94/-/format/auto/-/preview/1024x1024/-/quality/lighter/8.png)

You need to do that the same update on this file as well (From "nvme0n1p1" to "mmcblk0p1") (If you are using an SD card, you should see “/dev/mmcblk1p1”).

![https://ucarecdn.com/f2b14b27-a891-43fe-87e2-0dd92e1f66a7/-/format/auto/-/preview/1024x1024/-/quality/lighter/9.png](https://ucarecdn.com/f2b14b27-a891-43fe-87e2-0dd92e1f66a7/-/format/auto/-/preview/1024x1024/-/quality/lighter/9.png)

Then, save it & close.

Type "sudo reboot" to the terminal for applying the differences.

![https://ucarecdn.com/0fac459d-62ec-41fb-90e1-1c3217d26679/-/format/auto/-/preview/1024x1024/-/quality/lighter/10.png](https://ucarecdn.com/0fac459d-62ec-41fb-90e1-1c3217d26679/-/format/auto/-/preview/1024x1024/-/quality/lighter/10.png)

After the system rebooted, type "df -h". As you can see that, the eMMC connected as root.

![https://ucarecdn.com/b90d5a9b-54fc-4c2a-8107-04136e067b2d/-/format/auto/-/preview/1024x1024/-/quality/lighter/11.png](https://ucarecdn.com/b90d5a9b-54fc-4c2a-8107-04136e067b2d/-/format/auto/-/preview/1024x1024/-/quality/lighter/11.png)

## **Formatting the External Storage**

Now, open the "Disks" application (or type "gnome-disks" from terminal).

Select the SSD drive & format it.

![https://ucarecdn.com/1a9a17b4-1703-4f7f-ad0e-e6a34c236f02/-/format/auto/-/preview/1024x1024/-/quality/lighter/12.png](https://ucarecdn.com/1a9a17b4-1703-4f7f-ad0e-e6a34c236f02/-/format/auto/-/preview/1024x1024/-/quality/lighter/12.png)

Then, select the default settings & click “Format”.

![https://ucarecdn.com/10fbe2ac-c9f9-4e9b-96b0-336b4f67d2b4/-/format/auto/-/preview/1024x1024/-/quality/lighter/13.png](https://ucarecdn.com/10fbe2ac-c9f9-4e9b-96b0-336b4f67d2b4/-/format/auto/-/preview/1024x1024/-/quality/lighter/13.png)

Then, accept the formatting step.

![https://ucarecdn.com/76c1be0c-b250-4c6d-80fd-ce0d75102a7c/-/format/auto/-/preview/1024x1024/-/quality/lighter/14.png](https://ucarecdn.com/76c1be0c-b250-4c6d-80fd-ce0d75102a7c/-/format/auto/-/preview/1024x1024/-/quality/lighter/14.png)

Type the current user’s password on it.

![https://ucarecdn.com/4437ddce-e79e-478b-a1cb-376ef7c8b5c0/-/format/auto/-/preview/1024x1024/-/quality/lighter/15.png](https://ucarecdn.com/4437ddce-e79e-478b-a1cb-376ef7c8b5c0/-/format/auto/-/preview/1024x1024/-/quality/lighter/15.png)

After a few seconds later, the external storage formatted successfully.

![https://ucarecdn.com/7636c96e-9567-4400-bfe8-2b3460c26b15/-/format/auto/-/preview/1024x1024/-/quality/lighter/16.png](https://ucarecdn.com/7636c96e-9567-4400-bfe8-2b3460c26b15/-/format/auto/-/preview/1024x1024/-/quality/lighter/16.png)