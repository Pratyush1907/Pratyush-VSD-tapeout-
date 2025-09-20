# Pratyush-VSD-tapeout-
VSD Chip Tapeout 
# Chip Modelling and ASIC Design Flow

## 1. Chip Modelling (High-level Design Stage)

### Specs (C model)
- The very first stage is writing a functional model of the chip in a high-level language like **C/C++**.  
- This acts as the **golden reference model** – it describes **what the chip should do**, not how it will be implemented.

### Testbench in C
- A **testbench** is written in C to verify that the spec model works correctly.

### Output (O1)
- A **C model with testbench results** is the first checkpoint before RTL coding starts.


## 2. RTL Architecture (RTL Design Stage)

### Soft copy of hardware (Verilog/VHDL)
- The RTL architect takes the C model/specs and describes the hardware behavior using **RTL (Verilog or VHDL)**.  
- This is called the **soft model of hardware**.

### Components designed at RTL
- Processor core  
- Peripherals / IPs (like UART, SPI, timers, etc.)

### Synthesis process
- The RTL is synthesized to generate a **Gate-level Netlist** (logic gates + flip-flops).

### Macros & Analog IPs
- **Macros**: Pre-synthesized blocks (like memories, multipliers) which can be instantiated as required.  
- **Analog IPs**: Functional blocks that are not purely digital (PLL, ADC, etc.) described in functional RTL but implemented as hard macros.

### Output (O2)
- **Verified RTL description** of the entire SoC, ready for synthesis and integration.


## 3. SoC Integration (Chip-level Assembly Stage)

### Integration of all blocks
- Processor, peripherals, macros, and analog IPs are combined into one **SoC**.  
- **GPIOs and bus interconnects** are also added here.

### Backend (Physical design flow)
- Steps like **floorplanning, placement, clock tree synthesis (CTS), and routing** are performed.  
- Uses **hard macros (HM)** for analog and large IPs.  
- The processor can be included as **soft logic** (synthesized) or as a **hard macro** depending on the case.

### Output (O3)
- A **fully integrated SoC netlist/layout**.


## 4. Final ASIC Flow

### Conversion to GDSII
- The final physical layout is written out in **GDSII format** – the industry standard for chip fabrication.

### Checks before tapeout
- **DRC (Design Rule Check):** Ensures layout follows foundry rules.  
- **LVS (Layout vs. Schematic):** Ensures the layout matches the logical netlist.

### Tapeout
- After clean **DRC/LVS**, the **GDSII file** is sent to the fab for manufacturing.

### Tools that are going to be used 

## Yosys

sudo apt-get update
git clone https://github.com/YosysHQ/yosys.git
cd yosys
sudo apt install make        # If make is not installed
sudo apt-get install build-essential clang bison flex \
libreadline-dev gawk tcl-dev libffi-dev git \
graphviz xdot pkg-config python3 libboost-system-dev \
libboost-python-dev libboost-filesystem-dev zlib1g-dev
make config-gcc
make
sudo make install

<img width="1920" height="1080" alt="Screenshot from 2025-09-20 21-07-59" src="https://github.com/user-attachments/assets/1d46a4f9-dcc4-49c8-910e-6e0614f8fa82" />

## Icarus Verilog (iverilog)

sudo apt-get update
sudo apt-get install iverilog


<img width="1920" height="1080" alt="Screenshot from 2025-09-20 21-07-59" src="https://github.com/user-attachments/assets/e4e54d57-2d3f-45d0-b4f9-85013752b908" />

## GTKWave

sudo apt-get update
sudo apt-get install iverilog


<img width="1920" height="1080" alt="Screenshot from 2025-09-20 21-06-06" src="https://github.com/user-attachments/assets/e2b19424-eedc-4f9f-8f5e-3645fc79f866" />
<img width="1920" height="1080" alt="Screenshot from 2025-09-20 21-01-27" src="https://github.com/user-attachments/assets/b4849cc8-233a-44c7-a6df-fa4dc4d4e11c" />

## Ngspice

Download from Ngspice SourceForge
tar -zxvf ngspice-37.tar.gz
cd ngspice-37
mkdir release
cd release
../configure --with-x --with-readline=yes --disable-debug
make
sudo make install

<img width="1920" height="1080" alt="Screenshot from 2025-09-20 21-01-08" src="https://github.com/user-attachments/assets/addfe990-a20c-4ecb-922a-bb15ff5bffa7" />

## Magic

sudo apt-get install m4
sudo apt-get install tcsh
sudo apt-get install csh
sudo apt-get install libx11-dev
sudo apt-get install tcl-dev tk-dev
sudo apt-get install libcairo2-dev
sudo apt-get install mesa-common-dev libglu1-mesa-dev
sudo apt-get install libncurses-dev

git clone https://github.com/RTimothyEdwards/magic
cd magic
./configure
make
make install


<img width="1920" height="1080" alt="Screenshot from 2025-09-20 21-00-08" src="https://github.com/user-attachments/assets/3ec4968d-e3d2-4888-804d-eccc10e8c4f0" />

## OpenLANE

sudo apt-get update
sudo apt-get upgrade
sudo apt install -y build-essential python3 python3-venv python3-pip make git
sudo apt install apt-transport-https ca-certificates curl software-properties-common

Docker setup
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io
sudo docker run hello-world

Add user to docker group
sudo groupadd docker
sudo usermod -aG docker $USER
sudo reboot

 After reboot
docker run hello-world

<img width="1920" height="1080" alt="Screenshot from 2025-09-20 21-00-02" src="https://github.com/user-attachments/assets/a7a9fa40-7e45-446b-a73f-4cbeb2c468f4" />

## Dependency Check

git --version
docker --version
python3 --version
python3 -m pip --version
make --version
python3 -m venv -h

<img width="1920" height="1080" alt="Screenshot from 2025-09-20 20-59-32" src="https://github.com/user-attachments/assets/fe8942d3-0210-4fd6-9971-3c4796634497" />






