# Project Title

#  Verification of the SPI Protocol in System Verilog



## Project Overview

This project implements and verifies the Serial Peripheral Interface (SPI) protocol using SystemVerilog. The design includes an SPI Master that sends 12-bit data to a DAC through the SPI bus, and a testbench that verifies functionality using UVM-style modular components (driver, monitor, scoreboard, generator).
## Features

- SPI Master module for sending 12-bit data
- Fully synthesizable RTL code
- Testbench with:
- Generator: produces random 12-bit data
- Driver: drives SPI signals to DUT
- Monitor: monitors and captures SPI transactions
- Scoreboard: compares expected and actual data
- Supports new data signaling (newd), chip select (cs), serial clock (sclk), and mosi output
- Synchronous operation with clk and rst


## Architecture
The processor comprises modules including:
- spi_master.sv: Implements the SPI Master module that transmits 12-bit parallel input data (din) serially on the mosi line using a state machine. It controls cs (chip select) and sclk (serial clock) signals, and begins transmission when newd is asserted. The data is shifted out MSB-first, synchronized with the SPI clock..
- spi_master_results.txt: Contains the simulation output logs showing the sequence of SPI transactions. It records generated input data, data sent by the driver, data monitored from the DUT, and the scoreboard’s comparison results — helping verify correctness of the SPI protocol implementation..
- spi_master_tb.sv:  Testbench module that instantiates and connects the generator, driver, monitor, scoreboard, and interface. It controls the simulation flow, applies reset, generates the clock, and starts the verification process for the spi_master module.
- spi_slave.sv: Implements a simple SPI Slave module that receives serial data from the mosi line based on sclk and cs signals. It deserializes the incoming SPI data and reconstructs the original 12-bit word for monitoring and verification purposes during simulation.
- spi_verification_results.txt: Contains detailed simulation logs of the entire SPI protocol verification process. It includes messages from the generator, driver, monitor, and scoreboard showing data flow, comparisons, and pass/fail results of test cases.
- top.sv: Design top module that instantiates both the spi_master and spi_slave modules, connecting them with shared SPI signals (sclk, cs, mosi). Acts as the DUT for verifying end-to-end SPI communication.
- top_tb.sv: Top-level testbench that connects the test environment to the top design module. It initializes the simulation, applies reset and clock, and triggers the complete SPI verification flow.





## Run Locally

Clone the project

```bash
  git clone https://github.com/Priyanshu7900/-32-bit-RISC-V-single-cycle-processor-design-in-verilog.git

```

Go to the project directory

```bash
  cd -32-bit-RISC-V-single-cycle-processor-design-in-verilog
```

 Install a Verilog Simulator

```bash
 Download (Free with Intel FPGA tools): https://www.intel.com/content/www/us/en/software-kit/705184/modelsim-intel-fpgas.html
```

how to check the results on modelsim

```bash
  . Open ModelSim and Create a Project
  . vlib work
  . vmap work work 
  . vlog *.v 
  . vlog top_tb.v
  . vsim top_tb 
  . run -all
```
