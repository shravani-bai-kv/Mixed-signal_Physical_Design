# Prompt 03 - AMUX2_3V Macro Study

## Objective

Understand the analog macro used in the reference mixed-signal flow and identify the abstraction files required for integration into OpenLane.

## AI Tool

- Tool: ChatGPT
- Model: GPT-5.5

## Prompt

Explain the AMUX2_3V analog macro used in the repository.

Describe:

1. Function of the macro
2. Pin list
3. Signal pins
4. Power pins
5. LEF abstraction
6. LIB timing model
7. GDS layout
8. Verilog blackbox model
9. How OpenLane/OpenROAD treats the macro during implementation

---

## Summary of Response

AMUX2_3V is an analog 2:1 multiplexer implemented as a hard macro.

### Signal Pins

- A
- B
- SEL
- X

### Power Pins

- VPWR
- VGND

### Required Views

Verilog Blackbox provides module definition for synthesis while preventing modification of the analog circuitry.

#### LEF

Provides physical abstraction including:

- Macro dimensions
- Pin locations
- Routing blockages
- Placement information

#### LIB

Provides timing and power characterization used during synthesis and static timing analysis.

#### GDS

Contains the complete physical layout of the analog macro.

### OpenLane Integration

- During synthesis, the macro is treated as a blackbox.
- During floorplanning, placement and routing, OpenLane uses the LEF abstraction.
- During timing analysis, OpenROAD uses the LIB model.
- During final stream-out, the macro GDS is merged into the top-level GDS.

## Outcome

Established an understanding of the analog macro and its required abstraction views before AI-assisted file generation.
