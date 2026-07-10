# Prompt 04 - Macro File Inspection

## Objective

Inspect the actual abstraction files provided for the AMUX2_3V macro and understand how each view contributes to the mixed-signal RTL-to-GDS flow.

## AI Tool

- Tool: ChatGPT
- Model: GPT-5.5

## Prompt

For the AMUX2_3V analog macro, explain how the following files are used during the OpenLane/OpenROAD flow:

1. AMUX2_3V.v
2. AMUX2_3V.lef
3. AMUX2_3V.lib
4. AMUX2_3V.gds

For each file describe:

- Information contained
- Flow stage where it is used
- Consequences if the file is missing
- Interaction with the other abstraction views

---

## Summary of Response

### AMUX2_3V.v

- Used during synthesis as a blackbox model.
- Provides module declaration and pin connectivity while preventing synthesis from modifying the analog circuitry.

### AMUX2_3V.lef

Provides physical abstraction of the macro. Contains:

- Macro dimensions
- Pin geometry
- Pin layers
- Routing obstructions

Used during:

- Floorplanning
- Placement
- Routing

### AMUX2_3V.lib

Provides timing and power characterization. Used during:

- Timing-driven synthesis
- Static timing analysis
- Timing optimization

### AMUX2_3V.gds

Contains complete layout geometry. Used during:

- Final stream-out
- Physical verification
- Signoff

### Interaction Between Views

- Verilog defines connectivity 
- LIB defines timing
- LEF defines physical abstraction
- GDS defines final geometry

Together they allow an analog macro to participate in a digital implementation flow.

## Outcome

Established the purpose and interaction of the macro abstraction views used in the mixed-signal flow.
