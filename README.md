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
run the command `openroad -gui` 

## Steps to run the Design 
### Design 1 - gcd, Technology - nangate45
```
Step 1: Ubuntu terminal based on Linux OS installation.
Step 2: Type cd and press enter button
Step 3: source or_source.sh
Step 4: cd OpenROAD-flow-scripts/flow
Step 5: make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk
```
All the commands should be executed inside the flow directory for RTL-GDSII generation.
<div align = "center"><img width="518" alt="image" src="https://github.com/KAMATHAM19/OpenROAD-for-Low-cost-ASIC-design-and-Rapid-Innovation/assets/64173714/6f230ddf-e7ff-4042-a43d-61b06d8cdb45"></div>

## Steps to run the design stage by stage
To run the OpenROAD flow stage by stage, for synthesis, floorplan, placement, CTS, routing, and GDS-II generation, using the following commands.
1. Synthesis with yosys
```
   make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk synth
```
<div align = "center"><img width="935" alt="3" src="https://github.com/KAMATHAM19/OpenROAD-for-Low-cost-ASIC-design-and-Rapid-Innovation/assets/64173714/40f90a0b-3577-43b8-9eac-7b45ed3be238"></div>

2. Floorplan includes floorplan initialization/IO placement/Macro placement/Power planning
```
make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk floorplan
```
<div align = "center"><img width="930" alt="5" src="https://github.com/KAMATHAM19/OpenROAD-for-Low-cost-ASIC-design-and-Rapid-Innovation/assets/64173714/275db25e-67e3-4108-a874-8519b21baa0a"></div>

To see the floorplan in gui 
```
make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk gui_floorplan
```
<div align = "center"><img width="932" alt="image" src="https://github.com/KAMATHAM19/OpenROAD-for-Low-cost-ASIC-design-and-Rapid-Innovation/assets/64173714/9069d021-8e2d-4b15-9d89-47dc94edad87"></div>

3. Placement includes global placement/resizer/detail placement
```
make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk place
```
<div align = "center"><img width="931" alt="6" src="https://github.com/KAMATHAM19/OpenROAD-for-Low-cost-ASIC-design-and-Rapid-Innovation/assets/64173714/b2c790fc-4976-4bf7-9f6e-59bf8f661b9b"></div>
To see the placement in gui
```
make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk gui_place
```
<div align ="center"><img width="932" alt="7" src="https://github.com/KAMATHAM19/OpenROAD-for-Low-cost-ASIC-design-and-Rapid-Innovation/assets/64173714/717603df-8262-4635-b191-0da47b0da5e0"></div>

4. Clock Tree Synthesis (CTS) includes clock tree build/optimization
```
make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk cts
```
<div align ="center"><img width="932" alt="8" src="https://github.com/KAMATHAM19/OpenROAD-for-Low-cost-ASIC-design-and-Rapid-Innovation/assets/64173714/057d5d60-b9f0-4c67-83ca-5884589ae167"></div>

To see the CTS in gui
```
make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk gui_cts
```
<div align = "center"><img width="926" alt="9" src="https://github.com/KAMATHAM19/OpenROAD-for-Low-cost-ASIC-design-and-Rapid-Innovation/assets/64173714/ede4b6de-30e7-4aae-a7b8-ee31e71624be"></div>

5. Routing includes global routing/detail routing
```
make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk route
```
<div align = "center"><img width="931" alt="10" src="https://github.com/KAMATHAM19/OpenROAD-for-Low-cost-ASIC-design-and-Rapid-Innovation/assets/64173714/64db94be-e61d-4186-9011-f85a98fee7a0"></div>

To see the routing in gui
```
make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk gui_route
```
<div align = "center"><img width="931" alt="11" src="https://github.com/KAMATHAM19/OpenROAD-for-Low-cost-ASIC-design-and-Rapid-Innovation/assets/64173714/7acfe655-26dc-4ffa-bdfa-7c2bf57c1f5a"></div>

6. Finishing includes post-route timing extraction/GDSII generation with KLayout
```
make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk finish
```
<div align = "center"><img width="929" alt="12" src="https://github.com/KAMATHAM19/OpenROAD-for-Low-cost-ASIC-design-and-Rapid-Innovation/assets/64173714/cf7a4304-edfc-4fa0-8057-55d0df5fd1eb"></div>

To view the final GDSII in KLayout:

```
klayout -l platforms/nangate45/FreePDK45.lyp results/nangate45/gcd/base/6_final.gds
```
<div align = "center"><img width="931" alt="13" src="https://github.com/KAMATHAM19/OpenROAD-for-Low-cost-ASIC-design-and-Rapid-Innovation/assets/64173714/3a200772-912f-495e-be87-5b63b7c2c1f5"></div>

## Clean the previous run database
```
make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk clean_floorplan
```
To remove entire logs/results/reports for the specific run, use
```
make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk clean_all
```
## AutoTuner Installation
Autotuner-related commands should be executed from the flow/util directory.
```
pip3 install -U --user 'ray[default,tune]==1.13.0' ax-platform hyperopt nevergrad optuna pandas
pip3 install -U --user colorama==0.4.4 bayesian-optimization==1.4.0
```
To run autotuner for nangate45/gcd
```
cd util
python3.9 distributed.py --design gcd --platform nangate45 --config ../designs/nangate45/gcd/autotuner.json tune
```
To view Hyperparameter using Tensorboard
```
tensorboard --logdir=../logs/nangate45/gcd/test-tune-2024-012-11-47-27/
```
























## Reference

https://theopenroadproject.org/

https://github.com/The-OpenROAD-Project
