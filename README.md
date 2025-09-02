# Memory Module Simulation (RAM/ROM)

## Project Overview
This project demonstrates a simple **RAM module** in Verilog, simulating **read and write operations** with address decoding. It helps in understanding memory behavior in digital systems and modeling memory for simulation.

**What you'll learn:**
- Synchronous read/write operations
- Address decoding
- Memory modeling in Verilog

---

## Module: `memory_module.v`

**Inputs:**

| Name | Description |
|------|-------------|
| clk  | Clock signal |
| rst  | Reset signal (synchronous clear for `dout`) |
| we   | Write Enable (`1` = write, `0` = read) |
| addr | 4-bit memory address (16 locations) |
| din  | 8-bit data input |

**Outputs:**

| Name | Description |
|------|-------------|
| dout | 8-bit data output (read data or data being written) |

**Features:**
- 16 × 8-bit RAM
- Combinational read: `dout` shows data for current address immediately
- Synchronous write: data is written on the rising edge of `clk`

---

## Testbench: `tb_memory_module.v`

- Generates a 10 ns clock
- Performs writes to multiple addresses
- Performs reads from written addresses
- Monitors `WE`, `ADDR`, `DIN`, and `DOUT`

---

## Console Output Example

| Time  | WE | ADDR | DIN  | DOUT |
|-------|----|------|------|------|
| 0     | 0  | 0000 | 00   | 00   |
| 10000 | 1  | 0001 | AA   | AA   |
| 20000 | 1  | 0010 | 55   | 55   |
| 30000 | 1  | 0011 | FF   | FF   |
| 40000 | 0  | 0001 | FF   | AA   |
| 50000 | 0  | 0010 | FF   | 55   |
| 60000 | 0  | 0011 | FF   | FF   |

> **Note:** Times are in picoseconds (ps) according to the simulation timescale.

---

## How to Run
1. Open [EDA Playground](https://www.edaplayground.com/)
2. Create two files: `memory_module` and `tb_memory_module`
3. Copy the module and testbench code into their respective files
4. Run the simulation
5. Observe the console output

---

## Learning Outcomes
- Understanding **memory modeling** in Verilog
- Handling **read/write operations** using `we` and `addr`
- Observing **synchronous and combinational behavior** in simulation
