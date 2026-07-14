# Error 01 - AMUX2_3V GDS Investigation

## Problem Statement

During the Week 2 investigation, the absence of a standalone `AMUX2_3V.gds` file and the inability to immediately identify the macro in the final layout led to the initial assumption that the analog macro might not have been incorporated into the generated GDS.

---

## Investigation Strategy

Rather than relying only on visual inspection of the final layout, a complete RTL-to-GDS trace was performed.

The investigation followed the implementation flow:

```text
RTL
↓
Yosys Synthesis
↓
Floorplan
↓
Global Placement
↓
Detailed Routing
↓
DEF Database
↓
Final GDS
```

At each stage, the generated netlists and implementation databases were searched for the `AMUX2_3V` instance.

---

## Evidence Collected

The investigation confirmed the presence of the macro in:

* RTL source
* Synthesized netlist
* Floorplan netlist
* Global placement netlist
* Detailed routing netlist
* Routed DEF database
* Final GDS layout

The DEF database further confirmed that the macro was physically placed and connected to the expected signal nets.

---

## Root Cause

The initial conclusion resulted from relying primarily on visual inspection of the layout and the absence of a standalone `AMUX2_3V.gds` file.

However, the implementation flow preserves and places the analog macro throughout the physical design process even though no separate macro GDS file is referenced through the `EXTRA_GDS_FILES` configuration.

---

## Resolution

A complete stage-by-stage verification demonstrated that the `AMUX2_3V` macro successfully propagates through the entire implementation flow and is physically present in the final layout.

The Week 3 investigation therefore corrected the preliminary Week 2 assumption regarding the visibility of the analog macro.

---

## Final Outcome

**Status:** Resolved

The analog macro was verified from RTL through final GDS generation, providing confidence that the reproduced mixed-signal flow correctly preserves the analog IP throughout implementation.
