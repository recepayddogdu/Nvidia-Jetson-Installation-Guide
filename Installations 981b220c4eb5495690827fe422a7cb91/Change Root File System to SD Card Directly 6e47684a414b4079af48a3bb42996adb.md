# Change Root File System to SD Card Directly

## **How to format the SD card as ext4**

In this blog post, we will explain how to move your root file system on EMMC flash to SD card storage directly. The previous version of this post is here:

[https://www.forecr.io/blogs/bsp-development/changing-storage-of-the-root-file-system-emmc-to-sdmmc](https://www.forecr.io/blogs/bsp-development/changing-storage-of-the-root-file-system-emmc-to-sdmmc)

The advantage of this version is the boot up speed. In the previous version, the file system into the SD card mounted with a service after the file system into the eMMC mounted. This process increases the boot up time. In this post, the file system into the SD card mounted directly without any service. On the other hand, the Jetson module won’t boot up without SD card until the extlinux.conf file changed. To avoid this problem, you can backup your Jetson module before changing the root file system.

First, connect your SD card to SD card slot and connect the basic interfaces (Ethernet, HDMI, keyboard, mouse) then power on.

Open a terminal and type these commands below:

`sudo jetson_clocks`

`gnome-disks`

![https://ucarecdn.com/da707f55-e237-4bb1-b2ec-5449466b4b3e/-/format/auto/-/preview/1024x1024/-/quality/lighter/1.png](https://ucarecdn.com/da707f55-e237-4bb1-b2ec-5449466b4b3e/-/format/auto/-/preview/1024x1024/-/quality/lighter/1.png)

The first command allows the Jetson module’s whole sources to use. The next command opens GNOME Disks application below.

![https://ucarecdn.com/2460291c-dded-415a-a6f1-f435a81ac829/-/format/auto/-/preview/1024x1024/-/quality/lighter/2.png](https://ucarecdn.com/2460291c-dded-415a-a6f1-f435a81ac829/-/format/auto/-/preview/1024x1024/-/quality/lighter/2.png)

Create a new partition from SD card storage.

![https://ucarecdn.com/a85ff6cd-bdaa-4a02-be6c-19ca7e44561b/-/format/auto/-/preview/1024x1024/-/quality/lighter/3.png](https://ucarecdn.com/a85ff6cd-bdaa-4a02-be6c-19ca7e44561b/-/format/auto/-/preview/1024x1024/-/quality/lighter/3.png)

Format the disk as ext4 format (partition size is up to you but must be min current file system’s size).

![https://ucarecdn.com/28e640bd-2416-4aaf-9780-3b4552762be6/-/format/auto/-/preview/1024x1024/-/quality/lighter/4.png](https://ucarecdn.com/28e640bd-2416-4aaf-9780-3b4552762be6/-/format/auto/-/preview/1024x1024/-/quality/lighter/4.png)

After creating the partition, check it’s name (/dev/mmcblk1p1).

![https://ucarecdn.com/5409954b-11a0-43bb-be8b-bd2d0ec50433/-/format/auto/-/preview/1024x1024/-/quality/lighter/5.png](https://ucarecdn.com/5409954b-11a0-43bb-be8b-bd2d0ec50433/-/format/auto/-/preview/1024x1024/-/quality/lighter/5.png)

## **How to copy the root file system?**

Download the script file from **[here](https://github.com/recepayddogdu/Nvidia-Jetson-Installation-Guide/blob/main/sh_files/change_rootfs_storage_direct-emmc_to_sdmmc.sh)** ([Alternative](https://github.com/mistelektronik/forecr_blog_files/blob/master/change_rootfs_storage_direct-emmc_to_sdmmc.zip)) and extract it. Then, run it with this command below:

`sudo ./change_rootfs_storage_direct-emmc_to_sdmmc.sh {EXTERNAL_STORAGE}`

In our setup, we typed this command below:

`sudo ./change_rootfs_storage_direct-emmc_to_sdmmc.sh /dev/mmcblk1p1`

![https://ucarecdn.com/89483b5a-6e9f-4861-b3ab-880c0daad77e/-/format/auto/-/preview/1024x1024/-/quality/lighter/6.png](https://ucarecdn.com/89483b5a-6e9f-4861-b3ab-880c0daad77e/-/format/auto/-/preview/1024x1024/-/quality/lighter/6.png)

A few times later, the whole file system copied and the root path changed.

![https://ucarecdn.com/382621b0-45fe-458b-90cb-bf497a9eebe6/-/format/auto/-/preview/1024x1024/-/quality/lighter/7.png](https://ucarecdn.com/382621b0-45fe-458b-90cb-bf497a9eebe6/-/format/auto/-/preview/1024x1024/-/quality/lighter/7.png)

It’s time to reboot the Jetson module. Reboot it and check the Root File System copied successfully.

## **How to assign SD card as root file system?**

Open a terminal and type this command to check the root mounted from SD card below:

`df -h`

![https://ucarecdn.com/561ac64d-17e8-4246-be9f-685bff56deef/-/format/auto/-/preview/1440x1440/-/quality/lighter/8.png](https://ucarecdn.com/561ac64d-17e8-4246-be9f-685bff56deef/-/format/auto/-/preview/1440x1440/-/quality/lighter/8.png)

After rebooting you can see that the new storage is assigned as root file system.