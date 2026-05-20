# LDL1B Rev B — Fabrication Package

**Project:** Life Data Link (LDL1B) — Multimodal Vital Signs Monitor  
**Revision:** B  
**Product Code:** HZLDL1B  
**Author:** Jose Granados (josegranados@horizonmedical.co)  
**Generated:** May 20, 2026  

---

## PCB Specifications

| Parameter | Value |
|-----------|-------|
| Layers | 4 (F.Cu, In1.Cu, In2.Cu, B.Cu) |
| Board Dimensions | 62.45 × 72.44 mm |
| Material | FR4, 1.6 mm thickness |
| Copper Weight | 1 oz (35 µm) |
| Surface Finish | ENIG |
| Solder Mask | Green |
| Silkscreen | White |
| Min Track Width | 0.15 mm (6 mil) |
| Min Drill Size | 0.3 mm |
| Components | 92 (48 unique line items) |

---

## File Listing

### Gerber Files (`gerbers/`)

| File | Description | Extension Standard |
|------|-------------|-------------------|
| `LDL1B_revB-F_Cu.gtl` | Front Copper (Layer 1) | Protel |
| `LDL1B_revB-In1_Cu.g2` | Inner Copper 1 (Layer 2) | Protel |
| `LDL1B_revB-In2_Cu.g3` | Inner Copper 2 (Layer 3) | Protel |
| `LDL1B_revB-B_Cu.gbl` | Back Copper (Layer 4) | Protel |
| `LDL1B_revB-F_Mask.gts` | Front Solder Mask | Protel |
| `LDL1B_revB-B_Mask.gbs` | Back Solder Mask | Protel |
| `LDL1B_revB-F_Paste.gtp` | Front Solder Paste | Protel |
| `LDL1B_revB-B_Paste.gbp` | Back Solder Paste | Protel |
| `LDL1B_revB-F_SilkS.gto` | Front Silkscreen | Protel |
| `LDL1B_revB-B_SilkS.gbo` | Back Silkscreen | Protel |
| `LDL1B_revB-Edge_Cuts.gm1` | Board Outline | Protel |
| `LDL1B_revB-F_Fab.fab_front.gbr` | Front Fabrication Layer | Gerber |
| `LDL1B_revB-B_Fab.gbr` | Back Fabrication Layer | Gerber |

### Drill Files (`gerbers/`)

| File | Description | Format |
|------|-------------|--------|
| `LDL1B_revB-PTH.drl` | Plated Through Holes | Excellon |
| `LDL1B_revB-NPTH.drl` | Non-Plated Through Holes | Excellon |
| `LDL1B_revB-PTH-drl_map.gbr` | PTH Drill Map | Gerber |
| `LDL1B_revB-NPTH-drl_map.gbr` | NPTH Drill Map | Gerber |

### BOM (Bill of Materials)

| File | Format | Description |
|------|--------|-------------|
| `LDL1B_BOM.xlsx` | Excel | Full BOM with MPN, manufacturer, quantities |
| `LDL1B_BOM.csv` | CSV | Same data in CSV format |

### Pick-and-Place / Component Placement List

| File | Format | Description |
|------|--------|-------------|
| `LDL1B_CPL.csv` | CSV | Component positions, rotations, side |

### Assembly Documentation (`assembly/`)

| File | Description |
|------|-------------|
| `LDL1B_Top_Assembly.svg` | Top side assembly drawing (Fab + Silkscreen + Outline) |
| `LDL1B_Bot_Assembly.svg` | Bottom side assembly drawing (Fab + Silkscreen + Outline) |

---

## Layer Stack-Up

```
┌─────────────────────────────────────────┐
│  Front Silkscreen (F.SilkS)             │
│  Front Solder Mask (F.Mask)             │
├─────────────────────────────────────────┤
│  Layer 1: Front Copper (F.Cu)     1 oz  │
│  ─ ─ ─ ─ ─ ─ Prepreg ─ ─ ─ ─ ─ ─ ─   │
│  Layer 2: Inner Copper 1 (In1.Cu) 1 oz  │
│  ═══════════ Core (FR4) ═══════════════ │
│  Layer 3: Inner Copper 2 (In2.Cu) 1 oz  │
│  ─ ─ ─ ─ ─ ─ Prepreg ─ ─ ─ ─ ─ ─ ─   │
│  Layer 4: Back Copper (B.Cu)      1 oz  │
├─────────────────────────────────────────┤
│  Back Solder Mask (B.Mask)              │
│  Back Silkscreen (B.SilkS)             │
└─────────────────────────────────────────┘
Total thickness: ~1.6 mm
```

---

## Key Components

| Reference | Description | Package | Manufacturer |
|-----------|-------------|---------|--------------|
| U1 | BL654 BLE Module | XCVR Module | Laird Connectivity |
| U3 | ADS1292R ECG AFE | QFN-32 4×4mm | Texas Instruments |
| U6 | MAX30102 Pulse Oximeter | OLGA-14 3.3×5.6mm | Maxim Integrated |
| U5 | TMP117 Temperature Sensor | DSBGA-6 0.9×1.4mm | Texas Instruments |
| U8 | IIS2DLPC Accelerometer | LGA-12 2×2mm | STMicroelectronics |
| U2 | LP5907 3.3V LDO | SOT-23-5 | Texas Instruments |
| U7 | LP5907 1.8V LDO | SOT-23-5 | Texas Instruments |
| U4 | MCP73831 Li-Ion Charger | SOT-23-5 | Microchip |
| U9 | PCA9306 I2C Level Translator | X2SON-8 | Texas Instruments |
| J1 | USB-C Connector | JAE DX07S024XJ1 | JAE Electronics |

---

## Rev B Changes (from Rev A)

- Board layout and routing optimizations
- Component placement refinements
- Same core functionality: ECG (ADS1292R) + PPG (MAX30102) + Temperature (TMP117) + Accelerometer (IIS2DLPC) with BLE connectivity (BL654)

---

## Notes for Fabricator / Assembler

1. **Gerber Format:** Files use Gerber X2 format with Protel-standard extensions. Use file extensions (not embedded X2 attributes) for layer identification.
2. **Drill Format:** Excellon format, metric units, absolute coordinates.
3. **Component Placement:** CPL file uses millimeter units. Origin is board origin. Rotation is counterclockwise.
4. **Impedance Control:** Not specified. Standard 4-layer stack-up is acceptable.
5. **Special Components:** BL654 BLE module (U1) has integrated antenna — maintain keep-out zone per manufacturer datasheet. MAX30102 (U6) optical sensor requires clear optical path.
6. **Panelization:** No panelization specified. Fabricate as single boards.
7. **Testing:** Recommend E-test (electrical continuity test) on all boards.

---

## Verification Checklist

- [x] All copper layers present (4 layers)
- [x] Solder mask for both sides
- [x] Solder paste for both sides
- [x] Silkscreen for both sides
- [x] Board outline (Edge.Cuts)
- [x] Drill files (PTH + NPTH)
- [x] BOM matches CPL component count (92 components)
- [x] Pick-and-place file with positions and rotations
- [x] Assembly drawings for top and bottom

---

*Generated from KiCad 6 PCB source: `Lifedatalink_v1_revB.kicad_pcb`*
