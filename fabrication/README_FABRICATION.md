# Fabrication Files — LDL1B Rev B

**Generated:** 2026-05-20  
**Source:** `Lifedatalink_v1_revB_compat.kicad_pcb`  
**Tool:** KiCad 6.0.11 (pcbnew Python API)  

---

## Directory Structure

```
fabrication/
├── gerbers/
│   ├── LDL1B_revB-F_Cu.gtl          # Front Copper
│   ├── LDL1B_revB-In1_Cu.g2         # Inner Layer 1
│   ├── LDL1B_revB-In2_Cu.g3         # Inner Layer 2
│   ├── LDL1B_revB-B_Cu.gbl          # Back Copper
│   ├── LDL1B_revB-F_Mask.gts        # Front Solder Mask
│   ├── LDL1B_revB-B_Mask.gbs        # Back Solder Mask
│   ├── LDL1B_revB-F_Paste.gtp       # Front Paste/Stencil
│   ├── LDL1B_revB-B_Paste.gbp       # Back Paste/Stencil
│   ├── LDL1B_revB-F_SilkS.gto       # Front Silkscreen
│   ├── LDL1B_revB-B_SilkS.gbo       # Back Silkscreen
│   ├── LDL1B_revB-Edge_Cuts.gm1     # Board Outline
│   ├── LDL1B_revB-F_Fab.gbr         # Front Fabrication
│   ├── LDL1B_revB-B_Fab.gbr         # Back Fabrication
│   ├── LDL1B_revB-PTH.drl           # Plated Through Holes
│   └── LDL1B_revB-NPTH.drl          # Non-Plated Through Holes
├── assembly/
│   ├── LDL1B_revB_assembly_top.svg   # Top assembly drawing
│   └── LDL1B_revB_assembly_bottom.svg # Bottom assembly drawing
├── LDL1B_BOM.csv                     # Bill of Materials (CSV)
├── LDL1B_BOM.xlsx                    # Bill of Materials (Excel)
├── LDL1B_CPL.csv                     # Component Placement List
├── LDL1B_revB_gerbers.zip            # Complete Gerber+Drill archive
└── README_FABRICATION.md             # This file
```

## Gerber Format

- **Format:** Gerber X2 (RS-274X compatible)
- **Extensions:** Protel-style (.gtl, .gbl, .gts, etc.)
- **Coordinate format:** 4.6 (mm)
- **Drill format:** Excellon, mm units

## Design Rules Applied

| Parameter | Value |
|-----------|-------|
| Min track width | 0.1524 mm (6 mil) |
| Min clearance | 0.1524 mm (6 mil) |
| Min via drill | 0.2 mm |
| Via diameter | 0.4 mm |

## BOM Notes

- **U2:** LP5907MFX-3.3 (SOT-23-5) — schematic shows NCP167BMX330TBG (incompatible XDFN4 package)
- **U7:** LP5907MFX-1.8 (SOT-23-5) — schematic shows NCP167AMX180TBG (incompatible XDFN4 package)
- **U9:** PCA9306DQER — present on PCB, required for I²C level translation. Missing from schematic.

## How to Use

1. **PCB fabrication:** Upload `LDL1B_revB_gerbers.zip` to your fab house (JLCPCB, PCBWay, etc.)
2. **Stencil:** Use F_Paste (.gtp) and/or B_Paste (.gbp) layers
3. **Assembly:** Use `LDL1B_BOM.csv` + `LDL1B_CPL.csv` for pick-and-place
4. **Review:** See `DRC_REPORT.md` for known issues and `FABRICATION_READY_REPORT.md` for readiness assessment
