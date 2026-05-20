# Cambios de LDL1A a LDL1B

## Mejoras de PCB
1. **Plano de tierra continuo**: Capa 2 dedicada exclusivamente a GND
2. **Separación analógica/digital**: Mínimo 3 mm entre trazas
3. **Protección ESD**: TVS diodes en líneas SPI, I2C y GPIOTE
4. **Decoupling optimizado**: Caps de 100nF + 10µF por rail de alimentación
5. **Impedancia controlada**: 50Ω para traza de antena BLE
6. **Guard ring**: Anillo de guarda alrededor de entradas analógicas del ADS1292R

## Mejoras de Conectores
1. **Conector sensor PPG**: Migración de header a FPC 6-pin con mecanismo de lock
2. **Conector ECG**: Molex micro con retención (evita desconexión accidental)
3. **USB-C**: Reemplaza micro-USB para carga y debug

## Mejoras de Alimentación
1. **Regulador TPS62740**: Buck ultra-bajo Iq (360 nA) vs LDO anterior
2. **Cargador BQ25170**: USB-C con protección térmica integrada
3. **Monitorización de batería**: ADC del nRF52840 con divisor resistivo calibrado

## Mejoras para Sensores Centrales
1. **Cable FPC blindado**: Para sensor PPG remoto (carótida/axilar)
2. **Filtro EMI en I2C**: Ferrita + cap de 100pF en líneas SDA/SCL
3. **Pull-up ajustables**: Resistencias de pull-up I2C configurables (2.2kΩ / 4.7kΩ)
4. **Grommet de sellado**: Punto de salida del cable FPC con sellado de silicona
