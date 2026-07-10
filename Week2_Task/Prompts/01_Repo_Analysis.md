# Prompt 01 - Repository Analysis

## Objective

Understand the complete structure and workflow of the reference repository before attempting AI-assisted file generation.

## AI Tool

- Tool: ChatGPT
- Model: GPT-5.5

## Prompt

Analyze the GitHub repository:

https://github.com/praharshapm/vsdmixedsignalflow

Explain:

1. Top-level design
2. Analog macro used
3. RTL files
4. LEF files
5. LIB files
6. GDS files
7. OpenLane configuration
8. Physical design flow
9. Expected outputs

Provide the explanation as a dependency graph and implementation workflow.

---

## Summary of Response

The repository implements a mixed-signal RTL-to-GDS flow for the digital top module `design_mux`, which integrates the analog macro `AMUX2_3V`.

Key observations:

- RTL is synthesized using OpenLane/OpenROAD.
- The analog block is treated as a hard macro.
- LEF provides physical abstraction.
- LIB provides timing abstraction.
- GDS provides physical geometry.
- Verilog blackbox prevents synthesis from modifying the analog block.
- Floorplanning places the macro inside the digital design.
- Routing connects digital logic to the analog macro.
- Final outputs include DEF, GDS, reports and DRC/LVS results.

## Outcome

Successfully understood the complete mixed-signal flow before generating any files using AI.
