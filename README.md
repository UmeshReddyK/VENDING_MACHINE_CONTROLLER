🏪 Vending Machine Controller – UVM Verification Project
📌 Overview

This project focuses on the functional verification of a Vending Machine Controller (VMC) RTL design using SystemVerilog UVM methodology.

The RTL design (developed in Verilog HDL) models a configurable vending machine capable of handling up to 1024 items, each with programmable price and stock information.

The verification environment (developed in UVM) validates the correctness, robustness, and completeness of the VMC across a wide range of operational and corner-case scenarios, ensuring that the design is reliable for FPGA/ASIC deployment.

🛠️ Features
RTL Design (Verilog HDL)

Supports up to 1024 items with configurable memory.

Configuration Mode: Uses APB interface for dynamic programming of price & stock.

Operational Mode: Handles item selection, currency insertion, dispense, and change calculation.

Implements dual-port memory for safe clock-domain crossing.

FSM-based control for real-time response without software processors.

Verification Environment (SystemVerilog UVM)

Built using UVM layered architecture.

Agents implemented for:

APB Agent – drives/monitors APB transactions.

Currency Agent – models currency input.

Item Selection Agent – models user item selection.

Item Dispense Agent – monitors dispense and change outputs.

Scoreboard & Reference Model to check expected vs actual behavior.

Coverage-driven verification (functional + code coverage).

Supports directed + constrained-random testing.

Regression-ready with automated test execution and reporting.

✅ Testcases Implemented

Sanity Test – basic end-to-end transaction.

APB Read/Write Test – verifies configuration interface.

Multiple Currency Insertion – checks accumulation and correct dispense.

Multiple Item Transactions – validates stock decrement and dispense count.

Invalid Item Test – ensures correct handling of invalid or out-of-stock items.

Reset Test – validates reset clears internal states.

Concurrent User Test – stress test with overlapping transactions.

📊 Results

Achieved >95% functional coverage.

Verified correctness of:

Item selection and dispensing.

Currency accumulation and change calculation.

Stock decrement and inventory tracking.

Caught and validated edge cases (e.g., insufficient funds, invalid selection).

Delivered a scalable, reusable UVM environment for future vending machine designs.


🎯 Learning Outcomes

Practical experience with SystemVerilog UVM methodology.

Designed a self-checking, coverage-driven testbench.

Learned regression automation and result reporting.

Exposure to real-world SoC verification practices.

📜 License

Developed under the SURE Trust Internship Program.
Free to use for educational and learning purposes.
