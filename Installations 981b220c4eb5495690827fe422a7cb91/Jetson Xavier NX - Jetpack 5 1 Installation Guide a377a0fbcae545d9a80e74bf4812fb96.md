# Jetson Xavier NX - Jetpack 5.1 Installation Guide

> 1- Including the Kernel Files in Jetson OS Image
> 
> 
> 2- Installing the Jetson OS
> 
> 3- Installing the Jetson SDK Components
> 

**Download Nvidia SDK Manager**

[https://developer.nvidia.com/drive/sdk-manager](https://developer.nvidia.com/drive/sdk-manager)

(Alternative) [https://drive.google.com/file/d/149dG8AKdeF-fLJYwaIkmKIWpSomDgYgy/view?usp=share_link](https://drive.google.com/file/d/149dG8AKdeF-fLJYwaIkmKIWpSomDgYgy/view?usp=share_link)

---

In this tutorial, we will install JetPack-5.1 for DSBOX-NX2. First, we will include our Image, DTB & NVGPU kernel files in the Jetson OS image. Then, we will install the Jetson OS into the DSBOX-NX2. Finally, we will install the Jetson SDK components into it.

**Attention**: If you want to transfer the root file-system to an external drive, please **[format it](How%20to%20Clear%20The%20External%20Storage%20on%20Jetson%20Module%20fa019a382f0e49579dc71b92567ecfc1.md)** before starting this blog post.

## **Including the Kernel Files in Jetson OS Image**

Open the NVIDIA SDK Manager. Select “JetPack 5.1” for Target Operating System and “Jetson Xavier NX modules” for Target Hardware (The “Host Machine” components are not required). Then, continue to Step 2.

![https://ucarecdn.com/d63a4b3e-fb05-4e49-90fe-c6910978e138/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2012-42-47.png](https://ucarecdn.com/d63a4b3e-fb05-4e49-90fe-c6910978e138/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2012-42-47.png)

Choose only “Jetson Linux”, accept the terms & conditions and continue to Step 3.

![https://ucarecdn.com/94353141-b361-4347-8fb5-e565c87fa6e6/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2012-48-23.png](https://ucarecdn.com/94353141-b361-4347-8fb5-e565c87fa6e6/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2012-48-23.png)

The SDK Manager will ask the username’s password. Fill it and continue.

![https://ucarecdn.com/3f499039-e2b0-4b44-9bd3-c3582d962308/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2012-48-29.png](https://ucarecdn.com/3f499039-e2b0-4b44-9bd3-c3582d962308/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2012-48-29.png)

A few seconds later...

![https://ucarecdn.com/010a34fe-ec0d-4688-be3b-f475e4e30450/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2012-48-53.png](https://ucarecdn.com/010a34fe-ec0d-4688-be3b-f475e4e30450/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2012-48-53.png)

After the Jetson OS has created, the SDK Manager asks the Jetson module’s flashing style. Just skip it and exit from the SDK Manager.

![https://ucarecdn.com/89549338-08ad-458f-9940-a31a05d87163/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-02-22.png](https://ucarecdn.com/89549338-08ad-458f-9940-a31a05d87163/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-02-22.png)

![https://ucarecdn.com/23ecd750-9f7e-4bf1-a0c1-cb1fc839d6d9/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-02-28.png](https://ucarecdn.com/23ecd750-9f7e-4bf1-a0c1-cb1fc839d6d9/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-02-28.png)

Open the target HW image folder. (~/nvidia/nvidia_sdk/JetPack_5.1_Linux_JETSON_XAVIER_NX_TARGETS/Linux_for_Tegra/)

![https://ucarecdn.com/fc5d5a88-23fd-49be-912c-7d5a333c8783/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-43-24.png](https://ucarecdn.com/fc5d5a88-23fd-49be-912c-7d5a333c8783/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-43-24.png)

Download the BSP files from GitHub **[link](https://github.com/recepayddogdu/Nvidia-Jetson-Installation-Guide/raw/main/BSP_files/xavier_nx_JP5_1_bsp.tar.xz)** ([Alternative](https://github.com/mistelektronik/dsboard_nx2_xavier_nx_bsp/raw/master/xavier_nx_JP5_1_bsp.tar.xz)**)** and extract it.

![https://ucarecdn.com/444bd250-838e-48e3-838a-8375ca0f5f07/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-43-33.png](https://ucarecdn.com/444bd250-838e-48e3-838a-8375ca0f5f07/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-43-33.png)

Copy the pinmux file into the “bootloader/t186ref/BCT” folder.

![https://ucarecdn.com/454d4303-1e68-4542-a56f-b1bb24f93ac9/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-44-36.png](https://ucarecdn.com/454d4303-1e68-4542-a56f-b1bb24f93ac9/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-44-36.png)

Copy the “Image” file from the extracted folder to the “kernel” folder.

![https://ucarecdn.com/097463fc-50c8-4756-a15c-1941c285d97a/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-46-29.png](https://ucarecdn.com/097463fc-50c8-4756-a15c-1941c285d97a/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-46-29.png)

Then, copy the DTB file into the “kernel/dtb” folder.

**Attention**: If you use one of the previous DSBOARD-NX2 (rev-1.0, 1.1 & 1.21) carrier boards, please use the DTB file from the “without_fan” folder.

![https://ucarecdn.com/1e761f1f-d2b3-4dde-bca4-2951a9744edd/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-46-48.png](https://ucarecdn.com/1e761f1f-d2b3-4dde-bca4-2951a9744edd/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-46-48.png)

Return to the “JetPack_5.1_Linux_JETSON_XAVIER_NX_TARGETS” folder and copy the "nvgpu.ko" file.

![https://ucarecdn.com/1038914f-7971-41b1-8ae2-5a82642cc35d/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-47-04.png](https://ucarecdn.com/1038914f-7971-41b1-8ae2-5a82642cc35d/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-47-04.png)

Open a Terminal in the “Linux_for_Tegra” folder.

![https://ucarecdn.com/b5dbd8bd-4140-4eaa-a10e-bebbad82e712/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-47-19.png](https://ucarecdn.com/b5dbd8bd-4140-4eaa-a10e-bebbad82e712/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-47-19.png)

Create the system binaries with this command below:

`sudo ./apply_binaries.sh`

![https://ucarecdn.com/341c619e-e2c1-484c-8047-d4d75d860678/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-47-44.png](https://ucarecdn.com/341c619e-e2c1-484c-8047-d4d75d860678/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-47-44.png)

Update the NVGPU kernel file on the sample root file-system with this command below:

`sudo mv ../nvgpu.ko rootfs/usr/lib/modules/5.10.104-tegra/kernel/drivers/gpu/nvgpu/nvgpu.ko`

![https://ucarecdn.com/f9343382-1b42-4f83-9a21-7bb09b191163/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-49-10.png](https://ucarecdn.com/f9343382-1b42-4f83-9a21-7bb09b191163/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-49-10.png)

***Hint:*** If you want to configure your username-password & hostname with default settings, you can create user without the Ubuntu installation wizard. To do this, the user generation command structure should be:

`sudo tools/l4t_create_default_user.sh -u {USERNAME} -p {PASSWORD} -a -n {HOSTNAME} --accept-license`

For example (username:"nvidia", password:"nvidia", device-name:"nvidia-desktop"):

`sudo tools/l4t_create_default_user.sh -u nvidia -p nvidia -a -n nvidia-desktop --accept-license`

Then, create the system image with this command below:

`sudo ./flash.sh --no-flash jetson-xavier-nx-devkit-emmc mmcblk0p1`

![https://ucarecdn.com/667b71e5-d06e-4f32-bc0d-fbcb90eace11/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-49-34.png](https://ucarecdn.com/667b71e5-d06e-4f32-bc0d-fbcb90eace11/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-49-34.png)

A few seconds later …

![https://ucarecdn.com/ccdcee27-4fad-40cb-9fef-040bd135639b/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-50-35.png](https://ucarecdn.com/ccdcee27-4fad-40cb-9fef-040bd135639b/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-50-35.png)

## **Jetson OS Installation**

Connect the recovery USB (between installer PC & DSBOX-NX2's recovery USB) and power connection of your DSBOX-NX2.

While the DSBOX-NX2's power connector plugged in,

- press power button then wait for boot led lights up.
- press reset & recovery buttons together
- release reset button
- release the recovery button after 3 seconds later. This will set it to Recovery mode.

Then, type lsusb and check the device connected in Recovery mode (0955:7e19 NVidia Corp.)

![https://ucarecdn.com/b04154bd-f1a5-4853-b83c-f9852af940d1/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-52-18.png](https://ucarecdn.com/b04154bd-f1a5-4853-b83c-f9852af940d1/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-52-18.png)

Flash the Jetson OS with this script:

`sudo ./flash.sh -r jetson-xavier-nx-devkit-emmc mmcblk0p1`

![https://ucarecdn.com/4e28d95c-b1a4-4ba6-9088-aac77ded0033/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-52-32.png](https://ucarecdn.com/4e28d95c-b1a4-4ba6-9088-aac77ded0033/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2013-52-32.png)

At the end of the script, the device will reboot. Complete your Ubuntu installation wizard (if you have not created a user with *tools/l4t_create_default_user.sh* script file) from the DSBOX-NX2 (language, keyboard type, location, username & password etc.).

![https://ucarecdn.com/8245a12d-0e75-45c2-bed0-6a9a490661f5/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2014-01-34.png](https://ucarecdn.com/8245a12d-0e75-45c2-bed0-6a9a490661f5/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-21%2014-01-34.png)

To avoid kernel update with "apt upgrade" or "apt-get upgrade" commands, please follow [this guide](How%20to%20Apply%20Distro%20Upgrade%20(apt%20upgrade)%20on%20Jetso%2068549e38794044f98818fce4dce3cf2e.md) ([Alternative](https://www.forecr.io/blogs/bsp-development/how-to-apply-distro-upgrade-apt-upgrade-on-jetson-modules)) on the Jetson module.

## **Jetson SDK Components Installation**

**Attention**: Before starting this section, please transfer the Root File-System on an external storage. The eMMC storage i*s* not enough to install them. If you will use an NVME SSD storage, please follow **[this](Change%20Root%20File%20System%20to%20M%202%20SSD%20Directly%206946da0eca4040529ffbb368cc3187ae.md)** ([Alternatives](https://www.forecr.io/blogs/bsp-development/change-root-file-system-to-m-2-ssd-directly)) guide. If you will use an SD Card storage, please follow **[this](Change%20Root%20File%20System%20to%20M%202%20SSD%20Directly%206946da0eca4040529ffbb368cc3187ae.md)** ([Alternative](https://www.forecr.io/blogs/bsp-development/change-root-file-system-to-sd-card-directly)) guide.

***[Optional]*** Delete LibreOffice & ThunderBird packages (if you don’t need) and remove the unnecessary packages to increase the free space. To do this, type these commands to the DSBOX-NX2 side:

`sudo apt remove -y libreoffice* thunderbird*`

`sudo apt autoremove -ysudo apt clean`

Connect the DSBOX-NX2 to the Ethernet or connect its Recovery USB to the Host PC. Then, open the NVIDIA SDK Manager. Select “JetPack 5.1” for Target Operating System and “Jetson Xavier NX modules” for Target Hardware (The “Host Machine” components are not required). Then, continue to Step 2.

![https://ucarecdn.com/561e9ddd-d117-4a14-acc4-551ee04b7963/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-22%2009-30-51.png](https://ucarecdn.com/561e9ddd-d117-4a14-acc4-551ee04b7963/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-22%2009-30-51.png)

Choose only the “Jetson Runtime Components” ("Jetson SDK Components" are optional), accept the terms & conditions and continue to Step 3.

![https://ucarecdn.com/81c2485f-8b28-4702-93d5-3e5a60aa7e13/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-22%2009-32-25.png](https://ucarecdn.com/81c2485f-8b28-4702-93d5-3e5a60aa7e13/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-22%2009-32-25.png)

The SDK Manager will ask the username’s password. Fill it and continue.

![https://ucarecdn.com/07799567-7b02-4a7a-aab6-ccb6b9559e93/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-22%2009-34-50.png](https://ucarecdn.com/07799567-7b02-4a7a-aab6-ccb6b9559e93/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-22%2009-34-50.png)

Type the IP address, username and password of DSBOX-NX2 and Install the SDK Components.

![https://ucarecdn.com/b85fef5d-96f7-4fac-a155-5653165090cc/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-22%2009-35-12.png](https://ucarecdn.com/b85fef5d-96f7-4fac-a155-5653165090cc/-/format/auto/-/preview/1024x1024/-/quality/lighter/Screenshot%20from%202023-02-22%2009-35-12.png)

At the end of the installation, the DSBOX-NX2 becomes ready.

---

### Sources

1- [https://www.forecr.io/blogs/installation/jetpack-5-1-installation-for-dsbox-nx2](https://www.forecr.io/blogs/installation/jetpack-5-1-installation-for-dsbox-nx2)

1.1- [https://www.forecr.io/blogs/bsp-development/how-to-apply-distro-upgrade-apt-upgrade-on-jetson-modules](https://www.forecr.io/blogs/bsp-development/how-to-apply-distro-upgrade-apt-upgrade-on-jetson-modules)

1.2- [https://www.forecr.io/blogs/bsp-development/change-root-file-system-to-sd-card-directly](https://www.forecr.io/blogs/bsp-development/change-root-file-system-to-sd-card-directly)

[Other Sources](Jetson%20Xavier%20NX%20-%20Jetpack%205%201%20Installation%20Guide%20a377a0fbcae545d9a80e74bf4812fb96/Other%20Sources%208f717941c1aa418ab3c349f93144b78c.md)