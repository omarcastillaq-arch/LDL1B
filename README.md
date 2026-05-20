# LDL1B - Life Data Link v1 Revision B

## Monitor Multimodal de Signos Vitales · Hardware PCB Revisión B

### Descripción
LDL1B es la segunda revisión del hardware del monitor Life Data Link. Incluye mejoras de layout basadas en la experiencia con LDL1A, optimización de rutas de señal analógica, y soporte mejorado para sensores en sitios centrales.

### Mejoras respecto a LDL1A
| Aspecto | LDL1A | LDL1B |
|---------|-------|-------|
| Plano de tierra | Parcial | Continuo (capa 2 completa) |
| Separación analógica/digital | 1.5 mm | 3 mm mínimo |
| Conector sensor PPG | Header estándar | FPC 6-pin con lock |
| Conector ECG | Cable suelto | Molex micro con snap |
| Protección ESD | Básica | TVS en todas las líneas I/O |
| Conformal coating | Manual | Diseñado para aplicación selectiva |

### Componentes Principales

| Componente | Referencia | Función |
|-----------|-----------|---------|
| **nRF52840** | NORA-B106-00B (u-blox) | MCU + BLE 5.0 |
| **ADS1292R** | ADS1292RIPBSR (TI) | ECG AFE 24-bit |
| **MAX30102** | MAX30102EFD+ (Maxim) | PPG Red/IR |
| **Regulador** | TPS62740 | Buck 3.3V, ultra-low Iq |
| **Cargador** | BQ25170 | Cargador Li-Po USB-C |
| **Batería** | Li-Po 3.7V, 500 mAh | ~12 horas continuo |

### Esquema de Conexión de Sensores Centrales

```
                    LDL1B PCB Principal
                ┌─────────────────────────┐
                │                         │
  ECG Lead-I ──►│ J1 (Molex 4-pin)       │
  RA, LA, RL    │   → ADS1292R (SPI)     │
                │                         │
  PPG Carótida─►│ J2 (FPC 6-pin)         │
  o Axilar      │   → MAX30102 (I2C)     │
                │                         │
  USB-C ───────►│ J3 (USB-C)             │
  Carga + Debug │   → BQ25170 + UART     │
                │                         │
                │   nRF52840              │
                │   ┌───────┐             │
                │   │TIMER2 │ ← Sync 1MHz│
                │   │PPI    │             │
                │   │BLE 5.0│ → Antenna   │
                │   └───────┘             │
                └─────────────────────────┘
```

### Consideraciones de Diseño Mecánico para Humedad

#### Estrategia de Sellado
```
Vista en corte del enclosure:

    ┌─────────────────────────────┐
    │ Tapa superior (ABS médico)  │
    │  ┌─────────────────────┐   │
    │  │ Junta de silicona    │   │ ← O-ring perimetral
    │  └─────────────────────┘   │
    │  ┌─────────────────────┐   │
    │  │ PCB LDL1B            │   │
    │  │ (conformal coating)  │   │
    │  └─────────────────────┘   │
    │  ┌─────────────────────┐   │
    │  │ Batería Li-Po        │   │
    │  └─────────────────────┘   │
    │ Base inferior (ABS)         │
    └─────────────────────────────┘
          ↕
    Cable FPC a sensor PPG
    (sellado con grommet de silicona)
```

#### Niveles de Protección
| Zona | IP Rating | Método |
|------|-----------|--------|
| PCB | — | Conformal coating selectivo |
| Enclosure | IP54 | O-ring + sellado de conectores |
| Sensor PPG carotídeo | IP67 | Encapsulado + ventana óptica sellada |
| Sensor PPG axilar | IP67 | Nano-coating + encapsulado |
| Conector FPC | IP54 | Grommet de silicona en salida |

### Archivos del Repositorio
```
LDL1B/
├── README.md
├── .gitignore
├── Lifedatalink_v1_revB.kicad_prl
├── Libs/
│   └── Footprints/            ← Footprints personalizados
│       ├── 503480-0400.pretty/
│       ├── SeeedOPL-LED.pretty/
│       ├── MOLEX_503480-0600.pretty/
│       ├── SnapEda.pretty/
│       └── DF23.pretty/
└── docs/
    └── REVISION_B_CHANGES.md
```

### Repositorios Relacionados
- **[lifedatalink_firmware](https://github.com/jgrana2/lifedatalink_firmware)** - Firmware (compatible con LDL1A y LDL1B)
- **[LDL1A](https://github.com/jgrana2/LDL1A)** - Hardware revisión A
- **[LDL1A-DevKit](https://github.com/jgrana2/LDL1A-DevKit)** - Kit de desarrollo

### Licencia
MIT License - Copyright (c) 2020-2026 Life Data Link / Horizon Medical
