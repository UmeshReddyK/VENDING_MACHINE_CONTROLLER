# ​ Vending Machine Controller – UVM Verification Project

##  Overview  
This repository hosts the **Vending Machine Controller (VMC)** RTL design and its **functional verification environment**. The RTL, written in Verilog, supports up to **1024 programmable items** with dynamic configuration via an APB interface. The accompanying UVM-based testbench validates functionality, change calculation, and operational integrity across normal and corner cases.

For a quick demonstration of the VMC in action, you can explore the EDA Playground environment here:
- **Live Simulation**: [View and run on EDA Playground](https://edaplayground.com/x/WDaL)

---

##  Features  

### RTL Design (Verilog HDL)  
- **Up to 1024 items**: Each with configurable price and availability  
- **Configuration Mode**: Via APB interface (run on `pclk`)  
- **Operational Mode**: Handles item selection, currency insertion, dispense logic, change return  
- **Dual-Port Memory**: Safe crossing between configuration and operational clock domains  
- **FSM-Based Control**: Ensures deterministic, high-speed, real-time behavior  

### Verification Environment (SystemVerilog UVM)  
- Modular agents for:  
  - APB configuration (`apb_agent`)  
  - Currency input (`currency_agent`)  
  - Item selection (`item_sel_agent`)  
  - Output monitoring (`item_disp_agent`)  
- **Scoreboard reference model** for automated self-checking of correctness  
- **Coverage-driven verification** — both functional and code coverage  
- Supports both **directed** and **constrained-random** test stimulus  
- **Regression-ready** with automated simulation and reporting  

---
## 🧩 Testbench Architecture  

The UVM testbench is built with a **layered architecture**, making it modular, reusable, and scalable.  
It consists of four main agents (APB, Currency, Item Selection, and Dispense), connected through virtual interfaces and monitored by a central **Scoreboard**.  

Below is the high-level architecture of the testbench environment:  

![Testbench Architecture](docs/Tb_Architecture.png)  

- **APB Agent**: Drives and monitors APB configuration transactions.  
- **Currency Agent**: Models user currency insertion.  
- **Item Selection Agent**: Handles item selection transactions.  
- **Dispense Agent**: Monitors DUT outputs (dispensed item, change).  
- **Scoreboard**: Collects expected vs actual outputs and ensures correctness.  

##  Testcases Implemented  
-  **Sanity Test** – Basic end-to-end transaction  
-  **APB Interface Test** – Verification of configuration read/write  
-  **Multi-Currency Test** – Accumulation of funds and correct dispense  
-  **Multi-Item Test** – Sequential purchases verifying inventory management  
-  **Invalid Selection Test** – Handling of out-of-stock and invalid IDs  
-  **Reset Behavior Test** – Ensuring clean system reset clears state  
-  **Stress Test** – Overlapping user transactions to test robustness  

---

##  Results  
- Achieved **>95% functional coverage** across feature space  
- Verified correct:  
  - Item dispense logic  
  - Change calculation accuracy  
  - Inventory decrement and dispense count updates  
- Detected and validated all edge conditions (e.g., insufficient funds, invalid operations)  
- Delivered a **scalable, reusable UVM testbench** platform that can be extended to future SoC systems  

---
