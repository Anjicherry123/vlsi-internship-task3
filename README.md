---

## 🔧 Tools Used

- **Vivado (Xilinx)** – RTL design, simulation, and waveform analysis
- **Verilog HDL** – Hardware description language
- **Built-in waveform viewer** – For analysing simulation output

---

## 📦 Circuits Implemented

### 1. D Flip-Flop
Captures input `D` at every rising clock edge and transfers it to output `Q`. Simplest and most widely used flip-flop.

| Clock Edge | D | Q (Next State) |
|:---:|:---:|:---:|
| Rising ↑ | 0 | 0 |
| Rising ↑ | 1 | 1 |

**Files:** `src/d_flipflop.v`, `tb/tb_d_flipflop.v`

---

### 2. JK Flip-Flop
Two-input flip-flop supporting Set, Reset, Hold, and Toggle. Resolves the invalid state problem of the SR flip-flop when `J=1, K=1`.

| J | K | Q (Next State) |
|:---:|:---:|:---:|
| 0 | 0 | No change (Q) |
| 0 | 1 | Reset (0) |
| 1 | 0 | Set (1) |
| 1 | 1 | Toggle (~Q) |

**Files:** `src/jk_flipflop.v`, `tb/tb_jk_flipflop.v`

---

### 3. 4-bit Register
Stores 4 bits of data simultaneously using four D flip-flops sharing a common clock. Loads `D[3:0]` on every rising clock edge and holds the value until the next clock.

| Clock Edge | D[3:0] | Q[3:0] |
|:---:|:---:|:---:|
| Rising ↑ | 0000 | 0000 |
| Rising ↑ | 0001 | 0001 |
| Rising ↑ | 0111 | 0111 |
| Rising ↑ | 1111 | 1111 |
| Rising ↑ | 1010 | 1010 |

**Files:** `src/register4.v`, `tb/tb_register4.v`

---

### 4. 4-bit Binary Counter
Counts from `0` to `15` (binary `0000`–`1111`) and wraps back to `0`. Includes synchronous reset — forces count to `0000` when `reset=1`.

| Clock Cycle | Reset | count[3:0] |
|:---:|:---:|:---:|
| 1 | 1 | 0000 |
| 2 | 0 | 0001 |
| 3 | 0 | 0010 |
| 4 | 0 | 0011 |
| 5 | 0 | 0100 |
| 16 | 0 | 1111 |
| 17 | 0 | 0000 ↺ |

**Files:** `src/counter4.v`, `tb/tb_counter4.v`

---

## 🧪 Simulation & Verification

All circuits verified using testbench files in Vivado:
- Clock generated with `always #5 clk = ~clk` → **10 ns clock period**
- Input stimulus applied in `initial` block
- Outputs verified against expected truth tables using the built-in waveform viewer

---

## 📝 Key Observations

- All sequential circuits use `always @(posedge clk)` — making them fully **synchronous**
- **Non-blocking assignment** (`<=`) used throughout — correct RTL coding practice for flip-flop based circuits
- JK Flip-Flop toggle mode (`J=1, K=1`) resolves the undefined state of the SR flip-flop
- 4-bit counter wraps from `1111` → `0000` automatically due to natural overflow
- Output `Q` does not change between clock edges — only updates on rising edge

---

## 🚀 How to Run in Vivado

1. Open **Vivado** and create a new RTL project
2. Add source files from `src/` as design sources
3. Add testbench files from `tb/` as simulation sources
4. Set the corresponding testbench as the top module
5. Run **Behavioral Simulation**
6. Observe waveforms in the built-in viewer

---

## 📄 Report

Full internship report with simulation waveforms and truth tables:  
[`docs/Task3_VLSI_Report.pdf`](docs/Task3_VLSI_Report.pdf)

---

## 👤 Author

**VLSI Design Internship – Task 3**  
Tool: Vivado (Xilinx) | Language: Verilog HDL
