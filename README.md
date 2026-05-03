# VLSI Design Internship – Task 3
## Verilog RTL Design of Sequential Circuits and Flip-Flops

> Designed and simulated synchronous sequential circuits using Verilog HDL in Vivado (Xilinx).

---

## 📁 Repository Structure

    vlsi-task3/
    ├── src/
    │   ├── d_flipflop.v
    │   ├── jk_flipflop.v
    │   ├── register4.v
    │   └── counter4.v
    ├── tb/
    │   ├── tb_d_flipflop.v
    │   ├── tb_jk_flipflop.v
    │   ├── tb_register4.v
    │   └── tb_counter4.v
    ├── docs/
    │   └── Task3_VLSI_Report.pdf
    └── README.md

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
Counts from `0` to `15` (binary `0000` to `1111`) and wraps back to `0`. Includes synchronous reset — forces count to `0000` when `
