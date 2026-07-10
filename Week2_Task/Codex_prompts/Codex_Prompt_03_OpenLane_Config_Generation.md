# Codex Prompt 03 - OpenLane Configuration Generation

## Objective

Generate an OpenLane configuration file for integrating an analog hard macro into a digital design.

## Prompt

Generate a minimal OpenLane config.json for a mixed-signal design.

Requirements:

- Design name: design_mux
- Technology: SKY130A
- RTL files:
  - design_mux.v
  - raven_spi.v
- Analog macro:
  - AMUX2_3V

Include:

1. DESIGN_NAME
2. VERILOG_FILES
3. CLOCK_PORT
4. CLOCK_PERIOD
5. FP_CORE_UTIL
6. PL_TARGET_DENSITY
7. EXTRA_LEFS
8. EXTRA_LIBS
9. FP_PDN_MACRO_HOOKS

Output only valid JSON.

Do not include explanations.
