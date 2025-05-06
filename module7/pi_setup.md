# rasperry pi Setup

Steps to install ubuntu server on rasperry pi 

## Download Ubuntu server image 


### [ubuntu20.04 server arm64 Image Link](https://www.mediafire.com/file/f6mzpv2jm87ccmp/ubuntu-20.04.5-preinstalled-server-arm64%252Braspi_%25281%2529.img.xz/file)


##  use Etcher to boot the memory

### [Etcher link](https://etcher.balena.io/#download-etcher)


## Prepare Pi to connect with wifi
1. connect your pi with router using eathernet cable.

```bash
#to get the form of ip adress

ifconfig
```

```bash
sudo apt  install nmap
```
```bash
#to get the ip adress of your pi in the network  nmap -sn <IP FORM.*> 

nmap -sn 192.168.1.*

```
2. after connecting to your pi with ssh do the following

```bash
sudo apt update
sudo reboot 

```


```bash
sudo apt update

sudo apt  install network-manager
```

to connect with Wifi


```bash
nmcli device wifi list
```
```bash
nmcli device wifi connect <SSID> password <password>
```

```bash
nmcli connection show
```
Install Missing Depend_pkgs
```bash
cd ~/catkin_ws

rosdep install --from-paths src --ignore-src -r -y

```

##  sharing ROS Master on Multiple Machines [Robot-Laptop]

inside robot `.bashrc` file paste the following :

```bash
export ROS_MASTER_URI=http://<robot_Pi_IP>:11311

export ROS_IP=<robot_Pi_IP>
```
inside laptop `.bashrc` file paste the following :

```bash
export ROS_MASTER_URI=http://<robot_Pi_IP>:11311

export ROS_IP=<Laptop_IP>
```

