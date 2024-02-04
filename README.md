# OpenROAD for Low-cost ASIC design and Rapid Innovation

OpenROAD is an open-source tool that helps in designing integrated circuits (ICs). It is affordable, easy to use, and operates efficiently. The process it follows can run without constant human involvement, offering a 24-hour RTL-to-GDS-II capability for designing and creating ICs. This makes it a cost-effective and convenient option for exploring and implementation through tape-out.

The flow and the supported nodes in OpenROAD are

<div align = "center"><img width="412" alt="1" src="https://github.com/KAMATHAM19/OpenROAD-for-Low-cost-ASIC-design-and-Rapid-Innovation/assets/64173714/7eaa9c22-ad38-4be5-97a6-8090fa87a993"></div>


# Lab

## Prerequisites
1. Windows machine - 4GB RAM, 100GB Hard disk
2. Oracle Virtual box - 7.0.6 (https://www.virtualbox.org/wiki/Downloads)
3. Linux ubuntu - 22.04.1 (https://ubuntu.com/download/desktop)
4. Install Git - `sudo apt-get install git`
5. Install GCC compiler - `sudo apt-get install gcc g++`
6. Install Python - `sudo apt-get install python3`

 ## Klayout
 Install the required dependencies for the Klayout tool
 
```
sudo apt-get update; sudo apt-get upgrade; sudo apt install -y build-essential python3 python3-venv python3-pip make
sudo apt-get install make
sudo apt-get install qtbase5-dev qttools5-dev libqt5xmlpatterns5-dev qtmultimedia5-dev libqt5multimediawidgets5 libqt5svg5-dev
sudo apt-get install ruby ruby-dev
sudo apt-get install python3 python3-dev
sudo apt-get install libz-dev
sudo apt-get install libgit2-dev
```
Download the klayout from `https://www.klayout.de/build.html` depending on the Ubuntu version.

Install the klayout
```
wget https://www.klayout.org/downloads/Ubuntu-22/klayout_0.28.15-1_amd64.deb
sudo dpkg -i klayout_0.28.15-1_amd64.deb
```
## Yosys
Download the yosys from `https://github.com/YosysHQ/oss-cad-suite-build/releases/tag/2024-01-17`

Install the yosys
```
wget https://github.com/YosysHQ/oss-cad-suite-build/releases/download/2024-01-17/oss-cad-suite-linux-x64-20240117.tgz
tar -xzvf oss-cad-suite-linux-x64-20240117.tgz
```
## OpenROAD
Install the OpenROAD
```
wget https://github.com/Precision-Innovations/OpenROAD/releases/download/2024-01-16/openroad_2.0_amd64-ubuntu22.04-2024-01-16.deb
sudo apt install ./openroad_2.0_amd64-ubuntu22.04-2024-01-16.deb
git clone https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts.git
```
## Creating a Script file
1. Create the script file `gedit or_source.sh` and edit the locations of yosys and open_road. 

`which openroad -/usr/bin/openroad`

`which yosys - /home/venkat/Desktop/open_source/design/tools/yosys/oss-cad-suite/bin`

```
export OPENROAD_EXE=$(command -v /usr/bin/openroad)
export YOSYS_CMD=$(command -v /home/venkat/oss-cad-suite/bin/yosys)
export PATH="/home/venkat/oss-cad-suite/bin:$PATH"
```
2. Give permissions and modifications for the file
```
chmod 777 or_source.sh
```
3. Execute the script
```
source or_source.sh
```


openroad -gui

in openroad flow scripts 
cd openroad flow scripts/
git checkout master
git pull

cd flow
make


/home/venkat/OpenROAD-flow-scripts/flow/reports/nangate45/gcd/base


open_road - /home/venkat/Desktop/open_source/design/tools/open_road/OpenROAD-flow-scripts























Reference

https://theopenroadproject.org/
https://github.com/The-OpenROAD-Project
