# First steps

###  The ROCKPro64 charateristics are:
* Rockchip RK3399 Hexa-Core (dual ARM Cortex A72 and quad ARM Cortex A53) 64-Bit Processor with MALI T-860 Quad-Core GPU. 
* 4GB LPDDR4 system memory and 128Mb SPI boot Flash. 
* 16GB eMMC module and microSD slot for booting. 
* PCIe x4 open ended slot, 1x USB 3.0 type C Host with DP 1.2, 1x USB 3.0 type A Host, 2x USB 2.0 Host, Gigabit Ethernet.
* PI-2 GPIO Bus, MiPi DSI interface, eDP interface, touch Panel interface,  stereo MiPi CSI interface.
* Other peripheral device interface: UART, SPI, I2C.

## 1. Debian buster installation
Get the [latest version](https://github.com/ayufan-rock64/linux-build/releases) of Debian for the ROCKPro64 for GitHub.
You then need to get the operating system on the eMMC module. The eMMC module is a bit like an SD card, but you can’t plug it into you computer. However, you can plug it in the USB adapter you just bought.
Flash the downloaded image into the eMMC module with [etcher](https://www.balena.io/etcher/)
Put the eMMC into the board and plug the power connector, and wait 1 minute.

## 2. Connecting to the machine
Once started you can connect via SSH (first you should know the IP address the router has assigned it) using the user/password rockpro64.
The first time you login it will ask you to change the rocpro64 user password.

## 3. Checking for updates
Is one of the things I use to do:

```
sudo apt-get update
sudo apt-get upgrade
```
## 4. Configure a static IP
First, disable and stop NetworkManager.
```
rock64@rockpro64:~$ sudo su
[sudo] password for rock64: 
root@rockpro64:/home/rock64# systemctl stop NetworkManager
root@rockpro64:/home/rock64# systemctl disable NetworkManager
Removed /etc/systemd/system/multi-user.target.wants/NetworkManager.service.
Removed /etc/systemd/system/dbus-org.freedesktop.nm-dispatcher.service.
Removed /etc/systemd/system/network-online.target.wants/NetworkManager-wait-online.service.
```
Edit the file /etc/network/interfaces
```
iface eth0 inet static
    address 192.168.1.110
    broadcast 192.168.1.255
    netmask 255.255.255.0
    gateway 192.168.1.1
    dns-nameservers 192.168.1.5
```
Restart both networking and resolvconf to see the change take effect. 
```
# systemctl restart networking
# systemctl restart resolvconf
```


