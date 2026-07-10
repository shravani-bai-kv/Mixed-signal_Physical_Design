# Codex Prompt 02 - Analog Macro Analysis

## Objective

Understand the analog macro and identify all abstraction views required for OpenLane integration.

## Prompt

Analyze the analog macro AMUX2_3V.

Tasks:

1. Identify all available abstraction views.
2. Explain the purpose of:
   - Verilog view
   - LEF view
   - LIB view
   - Magic layout view
3. Extract macro pin information.
4. Classify pins as:
   - Signal pins
   - Power pins
5. Explain how OpenLane uses each abstraction.
6. Explain what happens if one abstraction is missing.

Output only:
- Pin table
- Abstraction summary table
- OpenLane integration workflow
- Missing-file impact analysis
