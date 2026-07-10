# Command Log 01 - Environment and Design Inspection

## Objective

Inspect the reproduced mixed-signal flow and identify the files, configurations and macro abstractions used by the implementation.

---

## Locate Pin Configuration Files

```bash
find . -iname "*pin*"
```

Purpose:

- Search for custom pin-order files
- Determine whether manual IO placement was used

Result:

- No custom pin-order file was found inside the design project

---

## Search for Configuration Files

```bash
find . -name "config.json"
```

Purpose:

- Locate OpenLane configuration files
- Identify the original design configuration

Result:

- Located design configuration and run-specific configuration snapshots

---

## Search for JSON Files Outside Run Directories

```bash
find . -name "*.json" | grep -v runs
```

Purpose:

- Identify the primary design configuration

Result:

- Located top-level config.json

---

## Inspect Design Configuration

```bash
cat config.json
```

Purpose:

- Review implementation parameters
- Identify LEF/LIB integration settings
- Identify PDN configuration

Result:

- Confirmed EXTRA_LEFS
- Confirmed EXTRA_LIBS
- Confirmed FP_PDN_MACRO_HOOKS

---

## Search for AMUX Files

```bash
find . -iname "*AMUX*"
```

Purpose:

- Locate macro abstraction files

Result:

- Found LEF
- Found LIB
- Found Verilog blackbox
