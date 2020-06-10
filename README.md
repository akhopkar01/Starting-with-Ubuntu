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
This sets python3 as your default python.
