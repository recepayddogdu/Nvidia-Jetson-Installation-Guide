# Change Root File System to M.2 SSD Directly

## **Formatting the M.2 SSD Storage**

In this blog post, we will explain how to move your root file system on EMMC flash to SSD storage on M.2 slot directly. The previous version of this post is here:

[https://www.forecr.io/blogs/bsp-development/changing-storage-of-the-root-file-system-emmc-to-m-2-ssd](https://www.forecr.io/blogs/bsp-development/changing-storage-of-the-root-file-system-emmc-to-m-2-ssd)

The advantage of this version is the boot up speed. In the previous version, the file system into the SSD mounted with a service after the file system into the eMMC mounted. This process increases the boot up time. In this post, the file system into the SSD mounted directly without any service. On the other hand, the Jetson module won’t boot up without SSD until the extlinux.conf file changed. To avoid this problem, you can backup your Jetson module before changing the root file system.

First, connect your M.2 compatible storage device to M.2 connector and connect the basic interfaces (Ethernet, HDMI, keyboard, mouse) then power on.

Open a terminal and type these commands below:

`sudo jetson_clocks`

`gnome-disks`

![https://ucarecdn.com/dcca260e-bd80-4ac0-987a-2b5649206824/-/format/auto/-/preview/1024x1024/-/quality/lighter/1.png](https://ucarecdn.com/dcca260e-bd80-4ac0-987a-2b5649206824/-/format/auto/-/preview/1024x1024/-/quality/lighter/1.png)

The first command allows the Jetson module’s whole sources to use. The next command opens GNOME Disks application below.

![https://ucarecdn.com/2ce502c6-9f8b-4a84-884a-cb5d5eae4419/-/format/auto/-/preview/1024x1024/-/quality/lighter/2.png](https://ucarecdn.com/2ce502c6-9f8b-4a84-884a-cb5d5eae4419/-/format/auto/-/preview/1024x1024/-/quality/lighter/2.png)

Create a new partition from SSD storage.

![https://ucarecdn.com/5b64d2f1-1521-460f-876e-66dd6f34d772/-/format/auto/-/preview/1024x1024/-/quality/lighter/3.png](https://ucarecdn.com/5b64d2f1-1521-460f-876e-66dd6f34d772/-/format/auto/-/preview/1024x1024/-/quality/lighter/3.png)

Format the disk as ext4 format (partition size is up to you but must be min current file system’s size).

![https://ucarecdn.com/b4bb351f-4843-4eb1-9855-955536386d9a/-/format/auto/-/preview/1024x1024/-/quality/lighter/4.png](https://ucarecdn.com/b4bb351f-4843-4eb1-9855-955536386d9a/-/format/auto/-/preview/1024x1024/-/quality/lighter/4.png)

After creating the partition, check it’s name (/dev/nvme0n1p1).

![https://ucarecdn.com/4a5e29ef-d6d7-4804-8acd-efb689c9db19/-/format/auto/-/preview/1024x1024/-/quality/lighter/5.png](https://ucarecdn.com/4a5e29ef-d6d7-4804-8acd-efb689c9db19/-/format/auto/-/preview/1024x1024/-/quality/lighter/5.png)

## **Copying the Root File System**

Download the script file from **[here](https://github.com/recepayddogdu/Nvidia-Jetson-Installation-Guide/blob/main/sh_files/change_rootfs_storage_direct-emmc_to_ssd.sh)** ([Alternative](https://github.com/mistelektronik/forecr_scripts/blob/master/change_rootfs_storage_direct-emmc_to_ssd.zip)) and extract it. Then, run it with this command below:

`sudo ./change_rootfs_storage_direct-emmc_to_ssd.sh {EXTERNAL_STORAGE}`

In our setup, we typed this command below:

`sudo ./change_rootfs_storage_direct-emmc_to_ssd.sh /dev/nvme0n1p1`

![https://ucarecdn.com/8b25f9e9-0f56-4694-a0f0-4c80cdfe4366/-/format/auto/-/preview/1024x1024/-/quality/lighter/6.png](https://ucarecdn.com/8b25f9e9-0f56-4694-a0f0-4c80cdfe4366/-/format/auto/-/preview/1024x1024/-/quality/lighter/6.png)

A few times later, the whole file system copied and the root path changed.

![https://ucarecdn.com/bb60e085-813f-498d-831d-e1018c03c5e8/-/format/auto/-/preview/1024x1024/-/quality/lighter/7.png](https://ucarecdn.com/bb60e085-813f-498d-831d-e1018c03c5e8/-/format/auto/-/preview/1024x1024/-/quality/lighter/7.png)

It’s time to reboot the Jetson module. Reboot it and check the Root File System copied successfully.

## **Assignment of the Root File System**

Open a terminal and type this command to check the root mounted from SSD below:

`df -h`

![https://ucarecdn.com/7f63b731-ffcd-43b6-bfe5-51d5d6a2678e/-/format/auto/-/preview/1920x1920/-/quality/lighter/8.png](https://ucarecdn.com/7f63b731-ffcd-43b6-bfe5-51d5d6a2678e/-/format/auto/-/preview/1920x1920/-/quality/lighter/8.png)

After rebooting you can see that the new storage is assigned as root file system.