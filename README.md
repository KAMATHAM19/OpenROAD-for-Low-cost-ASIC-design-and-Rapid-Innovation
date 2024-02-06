# OpenROAD for Low-cost ASIC design and Rapid Innovation

OpenROAD is an open-source tool that helps in designing integrated circuits (ICs). It is affordable, easy to use, and operates efficiently. The process it follows can run without constant human involvement, offering a 24-hour RTL-to-GDS-II capability for designing and creating ICs. This makes it a cost-effective and convenient option for exploring and implementation through tape-out.

The flow and the supported nodes in OpenROAD are

<div align = "center"><img width="622" alt="flow" src="https://github.com/KAMATHAM19/OpenROAD-for-Low-cost-ASIC-design-and-Rapid-Innovation/assets/64173714/8831d749-26c4-40d5-a8fa-27f78ccbd477"></div>

                                   Source:https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts

<div align = "center"><img width="412" alt="1" src="https://github.com/KAMATHAM19/OpenROAD-for-Low-cost-ASIC-design-and-Rapid-Innovation/assets/64173714/7eaa9c22-ad38-4be5-97a6-8090fa87a993"></div>

# Lab

## Prerequisites
1. Windows machine - 4GB RAM, 100GB Hard disk
2. Oracle Virtual box - 7.0.6 (https://www.virtualbox.org/wiki/Downloads)
3. Linux ubuntu - 22.04.1 (https://ubuntu.com/download/desktop)
4. Install Git - `sudo apt-get install git`
5. Install GCC compiler - `sudo apt-get install gcc g++`
6. Install Python - `sudo apt-get install python3`

## Yosys - Logic Synthesis
Download the yosys from `https://github.com/YosysHQ/oss-cad-suite-build/releases/tag/2024-01-17`

Install the yosys
```
wget https://github.com/YosysHQ/oss-cad-suite-build/releases/download/2024-01-17/oss-cad-suite-linux-x64-20240117.tgz
tar -xzvf oss-cad-suite-linux-x64-20240117.tgz
```

## OpenROAD - Floorplanning through Detailed Routing
Install the OpenROAD
```
wget https://github.com/Precision-Innovations/OpenROAD/releases/download/2024-01-16/openroad_2.0_amd64-ubuntu22.04-2024-01-16.deb
sudo apt install ./openroad_2.0_amd64-ubuntu22.04-2024-01-16.deb
git clone https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts.git
```

## Klayout - GDS merge, DRC and LVS (public PDKs)
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

### Design 2 - SPM, Technology - gf180

https://openroad-flow-scripts.readthedocs.io/en/latest/user/AddingNewDesign.html#adding-new-designs-to-the-orfs

Step 1: Create the Verilog source files directory based on the top module name.
```
cd OpenROAD-flow-scripts/flow/designs/src
mkdir spm
cd spm
vi spm.v
```
Step 2: Add verilog code into spm.v
```
// Copyright 2023 Efabless Corporation
//
// Licensed under the Apache License, Version 2.0 (the "License");
// you may not use this file except in compliance with the License.
// You may obtain a copy of the License at
//
//      http://www.apache.org/licenses/LICENSE-2.0
//
// Unless required by applicable law or agreed to in writing, software
// distributed under the License is distributed on an "AS IS" BASIS,
// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
// See the License for the specific language governing permissions and
// limitations under the License.

// (Parameterized) Unsigned Serial/Parallel Multiplier:
// - Multiplicand x (Input bit-serially)
// - Multiplier a (All bits at the same time/Parallel)
// - Product y (Output bit-serial)
module spm #(parameter bits=32) (
    input clk,
    input rst,
    input x,
    input[bits-1: 0] a,
    output y
);
    wire[bits: 0] y_chain;
    assign y_chain[0] = 0;
    assign y = y_chain[bits];

    wire[bits-1:0] a_flip;
    generate 
        for (genvar i = 0; i < bits; i = i + 1) begin : flip_block
            assign a_flip[i] = a[bits - i - 1];
        end 
    endgenerate

    delayed_serial_adder dsa[bits-1:0](
        .clk(clk),
        .rst(rst),
        .x(x),
        .a(a_flip),
        .y_in(y_chain[bits-1:0]),
        .y_out(y_chain[bits:1])
    );

endmodule

module delayed_serial_adder(
    input clk,
    input rst,
    input x,
    input a,
    input y_in,
    output reg y_out
);
    reg last_carry;
    wire last_carry_next;
    wire y_out_next;

    wire g = x & a;
    assign {last_carry_next, y_out_next} = g + y_in + last_carry;

    always @ (posedge clk or negedge rst) begin
        if (!rst) begin
            last_carry <= 1'b0;
            y_out <= 1'b0;
        end else begin
            last_carry <= last_carry_next;
            y_out <= y_out_next;
        end
    end
endmodule
```
Step 3: Create config.mk to define design configuration.
```
cd designs/gf180
mkdir spm
cd spm
vi config.mk
```
Step 4: Define key design parameters in config.mk
```
export PLATFORM         = gf180
export DESIGN_NAME      = spm
export VERILOG_FILES    = $(sort $(wildcard ./designs/src/$(DESIGN_NICKNAME)/*.v))
export SDC_FILE         = ./designs/$(PLATFORM)/$(DESIGN_NICKNAME)/constraint.sdc
export CORE_UTILIZATION = 40
export PLACE_DENSITY    = 0.60
export TNS_END_PERCENT  = 100
```
Step 5: Define SDC constraints
```
cd designs/gf180/spm
vi constraint.sdc
```
Edit as required to define design constraints
```
current_design spm
set clk_name  core_clock
set clk_port_name clk
set clk_period 10
set clk_io_pct 0.2

set clk_port [get_ports $clk_port_name]
create_clock -name $clk_name -period $clk_period  $clk_port
set non_clock_inputs [lsearch -inline -all -not -exact [all_inputs] $clk_port]

set_input_delay  [expr $clk_period * $clk_io_pct] -clock $clk_name $non_clock_inputs
set_output_delay [expr $clk_period * $clk_io_pct] -clock $clk_name [all_outputs]
```
Step 6: To run the flow with the make command and it will run synthesis, floorplan, placement, CTS, routing, and GDS-II generation.
```
make DESIGN_CONFIG=./designs/gf180/spm/config.mk
```
<div align = "center"><img width="934" alt="14" src="https://github.com/KAMATHAM19/OpenROAD-for-Low-cost-ASIC-design-and-Rapid-Innovation/assets/64173714/094e2d8a-a3b1-4d15-873c-cab4e41f9b80"></div>

SPM GDS-II layout in open-road

<div align = "center"><img width="932" alt="gf180" src="https://github.com/KAMATHAM19/OpenROAD-for-Low-cost-ASIC-design-and-Rapid-Innovation/assets/64173714/d28cdca3-b75a-445a-9319-c70f9e732c00"></div>

To view the final GDSII in KLayout:

<div align = "center"><img width="932" alt="15" src="https://github.com/KAMATHAM19/OpenROAD-for-Low-cost-ASIC-design-and-Rapid-Innovation/assets/64173714/bc0dae8e-589a-46b9-8c93-c26caac66195"></div>

## Reference

1. https://theopenroadproject.org/
2. https://github.com/The-OpenROAD-Project
3. https://openroad-flow-scripts.readthedocs.io/en/latest/user/UserGuide.html
4. https://vlsicad.ucsd.edu



![VENKAT KAMATHAM1](https://github.com/KAMATHAM19/OpenROAD-for-Low-cost-ASIC-design-and-Rapid-Innovation/assets/64173714/f6e8816d-8e43-41a7-9f9c-15da724c569a)
