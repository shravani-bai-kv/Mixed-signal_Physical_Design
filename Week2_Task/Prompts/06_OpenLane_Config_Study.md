# Prompt 06 - OpenLane Configuration Study

## Objective

Study the actual OpenLane configuration used for the mixed-signal design and identify the key parameters enabling analog macro integration.

## AI Tool

- Tool: ChatGPT
- Model: GPT-5.5

## Prompt

Analyze the OpenLane configuration used for the design_mux mixed-signal flow.

Explain:

1. Design inputs
2. Timing configuration
3. Floorplanning settings
4. Macro integration settings
5. PDN configuration
6. Why each parameter is required

---

## Configuration Inspected

```json
{
    "DESIGN_NAME": "design_mux",

    "VERILOG_FILES": [
        "dir::design_mux.v",
        "dir::raven_spi.v"
    ],

    "CLOCK_PORT": "select",
    "CLOCK_PERIOD": 10,

    "FP_CORE_UTIL": 20,
    "PL_TARGET_DENSITY": 0.4,

    "EXTRA_LEFS": [
        "dir::AMUX2_3V.lef"
    ],

    "EXTRA_LIBS": [
        "dir::AMUX2_3V.lib"
    ],

    "FP_PDN_MACRO_HOOKS": [
        "AMUX2_3V VPWR VGND VPWR VGND"
    ],

    "RUN_IRDROP_REPORT": false
}
```

## Findings

### DESIGN_NAME

Specifies the top-level module - design_mux

### VERILOG_FILES

Provides RTL sources:

- design_mux.v
- raven_spi.v

### CLOCK_PORT

Defines select as the timing reference signal.

### CLOCK_PERIOD

Specified as 10 ns for timing analysis and optimization.

### FP_CORE_UTIL

Core utilization = 20%
Provides sufficient whitespace for placement and routing.

### PL_TARGET_DENSITY

Placement density = 0.4
Reduces congestion around the analog macro.

### EXTRA_LEFS

Imports AMUX2_3V.lef for physical abstraction.

### EXTRA_LIBS

Imports AMUX2_3V.lib for timing characterization.

### FP_PDN_MACRO_HOOKS

Connects the analog macro power pins to the top-level power network.

### RUN_IRDROP_REPORT

Disabled in this flow.

## Outcome

Identified the critical OpenLane settings responsible for successful mixed-signal integration of the AMUX2_3V analog macro.
