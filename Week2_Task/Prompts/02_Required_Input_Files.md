# Prompt 02 - Required Input Files

## Objective

Identify all files required to reproduce the mixed-signal RTL-to-GDS flow.

## AI Tool

- Tool: ChatGPT
- Model: GPT-5.5

## Prompt

For reproducing the mixed-signal RTL-to-GDS flow of `design_mux` using SKY130 and OpenLane, list all required input files.

For each file explain:

1. Purpose
2. Whether it is mandatory or optional
3. Who generates it
4. Expected format
5. How OpenLane uses it

---

## Summary of Response

The following files were identified as necessary for the mixed-signal flow:

| File Type | Purpose |
|------------|----------|
| Verilog RTL | Digital design description |
| Verilog Blackbox | Prevents synthesis of analog macro |
| LEF | Physical abstraction of macro |
| LIB | Timing abstraction of macro |
| GDS | Physical layout of macro |
| OpenLane Config | Controls implementation flow |
| Pin Order File | Defines IO placement |
| SDC Constraints | Timing constraints |
| PDK Files | Technology definitions |

### Mandatory Inputs

- RTL Verilog
- Macro LEF
- Macro GDS
- Macro LIB
- Blackbox Verilog
- OpenLane Configuration
- SKY130 PDK

### Optional Inputs

- SDC constraints
- Additional floorplanning constraints
- Custom PDN configuration

## Outcome

Established the minimum file set required before beginning AI-assisted file generation.
