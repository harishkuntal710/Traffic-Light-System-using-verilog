# Traffic Light Controller Using Verilog HDL

## Project Overview

This project implements a traffic light controller using Verilog HDL and a Finite State Machine (FSM). The controller manages Red, Yellow, and Green traffic signals based on state transitions, a timer counter, reset, and enable control.

## Tools Used

- **Hardware Description Language:** Verilog HDL
- **Simulation Tool:** Icarus Verilog 12.0
- **Waveform Viewer:** EPWave (EDA Playground)

## Features

- Finite State Machine (FSM) based design
- One-hot state encoding
- Four states: OFF, RED, YELLOW, and GREEN
- Timer-based automatic signal transitions
- Active-low asynchronous reset (`rst_n`)
- Enable signal to control the traffic light sequence
- Testbench-based functional simulation
- Waveform analysis of internal and output signals

## State Encoding

| State  | Binary Encoding |
| ------ | --------------- |
| OFF    | `0001`          |
| RED    | `0010`          |
| YELLOW | `0100`          |
| GREEN  | `1000`          |

## Traffic Light Sequence

The controller follows these timer-based transitions:

- **OFF → RED:** When the enable signal is activated.
- **RED → YELLOW:** When the timer reaches 50.
- **YELLOW → GREEN:** When the timer reaches 10.
- **GREEN → RED:** When the timer reaches 30.
- **Any state → OFF:** When the enable signal is deactivated.

The timer values represent clock counts, not seconds. Actual timing depends on the clock frequency and counter implementation.

## Project Files



- traffic_light_fsm_code.txt — Verilog testbench and Verilog FSM design.
- `waveform.png` — Simulation waveform screenshot.



## Simulation and Verification

The design was simulated using Icarus Verilog 12.0. The testbench generates a clock, applies reset and enable signals, and observes the traffic light controller's behavior.

The simulation waveform shows:

- Clock and reset signals
- Enable control
- Current and next FSM states
- Timer counter and timer-clear signal
- Red, Yellow, and Green outputs

The waveform can be used to inspect state transitions and verify the controller's operation.

## How to Run the Simulation

Make sure both the design and testbench files are available in the same directory.

**1. Compile the design and testbench**

```bash
iverilog -g2012 -o traffic_light_fsm_code.v traffic_light_fsm_code_tb.v
```

**2. Run the simulation**

```bash
vvp traffic_sim
```

**3. View the waveform**

The testbench generates a VCD waveform file using `$dumpfile` and `$dumpvars`. Open the generated `dump.vcd` file in GTKWave or another compatible waveform viewer.

## Learning Outcomes

- Understanding FSM design using Verilog HDL
- Implementing one-hot state encoding
- Designing timer-controlled sequential logic
- Writing a Verilog testbench
- Simulating and analyzing digital circuits

## Author

Harish Kuntal

## Project Type

Just a learning project

