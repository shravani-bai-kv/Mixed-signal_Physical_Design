# Codex Prompt 06 - Power Connectivity Debug

## Objective

Debug power-grid connectivity issues between a top-level design and an analog hard macro.

## Prompt

An OpenLane mixed-signal design reports power connectivity warnings for an analog macro.

Macro:

- AMUX2_3V

Power Pins:

- VPWR
- VGND

Tasks:

1. Identify possible causes of power connectivity warnings.
2. Verify FP_PDN_MACRO_HOOKS syntax.
3. Verify LEF power pin definitions.
4. Verify macro power-net naming consistency.
5. Verify PDN generation settings.
6. Explain how OpenROAD connects macro power pins.
7. Generate a systematic debugging workflow.

Output only:

- Root-cause checklist
- Verification checklist
- Debug workflow
- Recommended fixes
