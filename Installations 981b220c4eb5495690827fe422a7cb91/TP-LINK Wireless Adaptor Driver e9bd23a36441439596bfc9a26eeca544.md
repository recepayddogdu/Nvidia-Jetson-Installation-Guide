# TP-LINK Wireless Adaptor Driver

[TP-Link AC600 Archer T2U Plus driver for Ubuntu 20.04](https://askubuntu.com/questions/1376835/tp-link-ac600-archer-t2u-plus-driver-for-ubuntu-20-04/1376844#1376844)

```
sudo apt install git dkms
git clone https://github.com/aircrack-ng/rtl8812au.git
cd rtl8812au
sudo make dkms_install
```