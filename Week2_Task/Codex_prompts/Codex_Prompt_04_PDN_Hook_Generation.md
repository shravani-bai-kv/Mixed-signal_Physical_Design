# Codex Prompt 04 - PDN Hook Generation

## Objective

Generate OpenLane PDN hook configuration for an analog hard macro.

## Prompt

An analog macro named AMUX2_3V is integrated into a SKY130 OpenLane design.

Power Pins:

* VPWR
* VGND

Generate the correct FP_PDN_MACRO_HOOKS entry.

Requirements:

1. Connect macro VPWR to top-level VPWR.
2. Connect macro VGND to top-level VGND.
3. Use OpenLane-compatible syntax.

Output only the JSON snippet.

## Expected Output

```json
{
    "FP_PDN_MACRO_HOOKS": [
        "AMUX2_3V VPWR VGND VPWR VGND"
    ]
}
```

## Purpose

This prompt generates the PDN hook configuration required to connect the AMUX2_3V analog macro to the top-level power distribution network during OpenLane implementation.

## Verification

The generated output was compared against the working mixed-signal implementation and matched the configuration used in the reproduced flow.

## Outcome

Successfully generated a valid OpenLane PDN hook configuration for analog macro integration.
