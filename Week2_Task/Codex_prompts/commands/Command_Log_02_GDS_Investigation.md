# Command Log 02 - GDS Integration Investigation

## Objective

Investigate how the AMUX2_3V analog macro is represented in the reproduced mixed-signal flow and determine whether a dedicated macro GDS is used.

---

## Search for Macro Files

```bash
find . -iname "*AMUX*"
```

Purpose:

- Locate all available macro abstraction files

Result:

Found:

- AMUX2_3V.v
- AMUX2_3V.lef
- AMUX2_3V.lib

No AMUX2_3V.gds file was found.

---

## Search for GDS Files

```bash
find . -iname "*.gds"
```

Purpose:

- Identify generated GDS outputs

Result:

Found:

- design_mux.magic.gds

---

## Search for GDS References

```bash
grep -R "\"EXTRA_GDS" .
```

Purpose:

- Determine whether any stage of the flow referenced a macro GDS file

Result:

All stages reported:

```json
"EXTRA_GDS_FILES": null
```

---

## Search for Macro References

```bash
grep -R "AMUX2_3V" config.json
```

Purpose:

- Verify macro integration settings

Result:

Confirmed:

- EXTRA_LEFS
- EXTRA_LIBS
- FP_PDN_MACRO_HOOKS

---

## KLayout Hierarchy Inspection

Procedure:

1. Opened design_mux.magic.gds
2. Examined cell hierarchy
3. Inspected child cells under design_mux

Result:

Observed:

- sky130_fd_sc_hd_* standard cells

Did not observe:

- AMUX2_3V cell instance

---

## Conclusion

The reproduced flow successfully generated a final GDS.

The implementation relied on:

- Verilog abstraction
- LEF abstraction
- LIB abstraction

No standalone macro GDS file was used during implementation.

---

## Updated Conclusion

The GDS investigation confirmed that no standalone `AMUX2_3V.gds` file is provided within the reproduced implementation flow and that the OpenLane configuration does not reference any external macro GDS through `EXTRA_GDS_FILES`.
At the time of the Week 2 investigation, this prevented a definitive conclusion regarding how the analog macro was represented in the final layout.
A subsequent Week 3 RTL-to-GDS trace resolved this question by verifying that the `AMUX2_3V` macro is preserved throughout synthesis, floorplanning, placement, detailed routing and DEF generation, and is identifiable in the generated layout. Therefore, this command log documents the initial investigation, while the complete verification is presented in the Week 3 command log and observations.
