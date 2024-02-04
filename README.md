# OpenROAD for Low-cost ASIC design and Rapid Innovation
 This workshop was organised by IIT Guwahati collabarted with MeitY, NINE Labs, Electronics India.


OpenROAD is an open-source tool that helps in designing integrated circuits (ICs). It is affordable, easy to use, and operates efficiently. The process it follows can run without constant human involvement, offering a 24-hour RTL-to-GDS-II capability for designing and creating ICs. This makes it a cost-effective and convenient option for exploring and implemention through tapeout.


`sudo apt-get update; sudo apt-get upgrade; sudo apt install -y build-essential python3 python3-venv python3-pip make`

2. install klayout - https://www.klayout.de/build.html depend on ubuntu version download according to it

`wget https://www.klayout.org/downloads/Ubuntu-22/klayout_0.28.15-1_amd64.deb`

```sudo apt-get install gcc g++ make
sudo apt-get install qtbase5-dev qttools5-dev libqt5xmlpatterns5-dev qtmultimedia5-dev libqt5multimediawidgets5 libqt5svg5-dev
sudo apt-get install ruby ruby-dev
sudo apt-get install python3 python3-dev
sudo apt-get install libz-dev
sudo apt-get install libgit2-dev```

`sudo dpkg -i klayout_0.28.15-1_amd64.deb`

3. install yosys - https://github.com/YosysHQ/oss-cad-suite-build/releases/tag/2024-01-17 

`wget https://github.com/YosysHQ/oss-cad-suite-build/releases/download/2024-01-17/oss-cad-suite-linux-x64-20240117.tgz`

`tar -xzvf oss-cad-suite-linux-x64-20240117.tgz`

4. openroad - `wget https://github.com/Precision-Innovations/OpenROAD/releases/download/2024-01-16/openroad_2.0_amd64-ubuntu22.04-2024-01-16.deb`

`sudo apt install ./openroad_2.0_amd64-ubuntu22.04-2024-01-16.deb`

5. git clone https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts.git

path for script file 

which openroad -/usr/bin/openroad

yosys location - /home/venkat/Desktop/open_source/design/tools/yosys/oss-cad-suite/bin

open_road - /home/venkat/Desktop/open_source/design/tools/open_road/OpenROAD-flow-scripts

create file - gedit or_source.sh

export OPENROAD_EXE=$(command -v /usr/bin/openroad)
export YOSYS_CMD=$(command -v /home/venkat/oss-cad-suite/bin/yosys)
export PATH="/home/venkat/oss-cad-suite/bin:$PATH"

chmod 777 or_source.sh - giving permission

source or_source.sh - execute

openroad -gui

in openroad flow scripts 
cd openroad flow scripts/
git checkout master
git pull

cd flow
make


/home/venkat/OpenROAD-flow-scripts/flow/reports/nangate45/gcd/base


























Reference

https://theopenroadproject.org/
https://github.com/The-OpenROAD-Project