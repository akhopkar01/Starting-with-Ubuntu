# About this Repository
For Windows Users who are diving into Ubuntu, This is an instructional guide to install Packages and getting started with Ubuntu. This guide will instruct on getting the necessary packages for Ubuntu 16.04 LTS. This instructions could be used for Ubuntu of higher distro versions too. The packages to be included includes: 
- Python3
- pip
- Git
- ROS
- NVIDIA Drivers

About my system:
- Computer : Lenovo LEGION Y545
- GPU : NVIDIA GeFORCE GTX 1660Ti

Considering that you have just installed Ubuntu, One of the few problems prevelant is that of getting the WiFi working. Click the WiFi icon and Click 'Enable WiFi', if WiFi networks are not detected. Connect ethernet to the system as we will require internet to update Ubuntu drivers. We need to allow Ubuntu have updates. Go to **Software & Updates > Ubuntu Software** : Enable "_main, universe, restricted, multiverse_" (For more info about them: https://help.ubuntu.com/community/Repositories/Ubuntu).
Then,
```
sudo apt-get update && sudo apt-get upgrade
```

## Python3
It is advisable to use Python3 over Python2, Ubuntu 16.04 comes with Python3 and Python2 by default. We can replace Python2 with Python3 to make our default Python version. Follow the instructions as follows:
```
python3 --version
sudo apt-get purge python2*
sudo apt autoremove
```
This checks the latest version of Python3 and Removes Python2 with its dependencies, to avoid conflict in future steps.
```
echo "alias python=python3" >> ~/.bash_aliases
source ~/.bash_aliases
sudo apt update
python --version
```
This sets python3 as your default python. You can write your first Python program using a text editor. 
Suggested: Sublime text
```
wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
sudo apt-get update && sudo apt-get install sublime-text
```

## pip
Now having Python3 up and running, it is very easy to install pip. 
```
sudo apt-get install python-pip
```
It is often advisable to start Python programming with virtual environments, which are offered by PyCharm and Anaconda.

### PyCharm
PyCharm is a powerful python IDE which provides strong virtual environment encapsulation. Download PyCharm from: https://www.jetbrains.com/pycharm/download/#section=linux. Download any of the two versions (Community/Pro). I personally choose to use PyCharm Community
```
cd Downloads/
tar -xzf pycharm-community-2018.1.4.tar.gz
cd pycharm-community-2018.1.4
cd bin
sh pycharm.sh
```
This will install PyCharm for you.

### Anaconda
Download Anaconda from: https://www.anaconda.com/download/#linux > Copy the package to home folder and run,
```
bash ./Anaconda3-5.1.0-Linux-x86_64.sh
```
This will get Anaconda for you.

## Git
If you're a developer or want to contribute to git community it is necessary that you maintain Git in your local system.
```
sudo apt-get update
sudo apt-get install git-core
git --version
git config --global user.name "YourGithubUserName"
git config --global user.email "YourGithubEmail"
cat ~/.gitconfig
```

## ROS
It is highly recommended to follow ROS Installation official documentation: http://wiki.ros.org/kinetic/Installation/Ubuntu. Or clone this repo. and follow these commands (ROS-kinetic-desktop-full):
```
cd ~/Starting-with-Ubuntu
./ros_install.sh
```

## NVIDIA Driver
First, Go to **Software & Updates > Additional Drivers**, Select the NVIDIA-xxx (proprietary), then Apply Changes and restart the computer. 
Try checking for the driver by command: ```nvidia-smi``` in the terminal.

If you can't see any NVIDIA drivers, Follow the following steps in terminal:
```
lspci | grep VGA
uname -r
```
To know about your graphic card vendor and kernel version of the system. It is important that the driver is compatible with your kernel version. Follow the instructional guide only if you have NVIDIA GPU.

We first remove any trace of nvidia from the system:
```
sudo apt-get update
sudo apt-get purge nvidia*
sudo apt-get autoremove
```

We now add the pakcage archive repository maintained by NVIDIA
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
```
You can validate this by checking **Software & Updates > Other Updates**, You can see the ppa added to the list.
You may find the compatible NVIDIA driver for your system: https://www.nvidia.com/Download/index.aspx
Mine is NVIDIA 430.64
Now you may do : 
```
sudo ubuntu-drivers autoinstall
```
This autoinstalls from the added package archives the stable nvidia driver version or you may install specific compatible driver
```
sudo apt-get install nvidia-xxx
```
Now the terminal will prompt a message with the heading of **Configuring Secure Boot**
You need to enter the terminal input prompt by $ Ctrl + Scroll-Down $. The prompt will ask you to setup your password.
Post which you may `$ reboot` the system. During the reboot the system will enter the SHIM UEFI Management screen.
Press `Enter` to enter the MOK Management. In here, You may get the option: *Change Secure Boot* or *Enroll MOK Key*. Enter the password you set in the terminal. Login to your Ubuntu System. 

Congrats! You're done with your start-up Ubuntu camp!!
