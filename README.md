# Duino-Coin Solar Miner Project
## Project Description

The project consists of:

1. A **miner based on ESP32-WROOM**
2. An **off-grid battery system using 21700 cells**
3. A **36W solar panel with a separate energy storage module**

The goal of this project is to mine **Duino-Coin in an energy-efficient and off-grid way**, without relying on the electrical grid.

---

# Miner

![Miner](/imgs/miner.jpg)

- 3 × **ESP32-WROOM modules**
- **5V cooling fan**
- Average power usage: **1500 mAh per hour**
- Mining performance: **~1.14 Duino-Coin per hour**
- Stable performance: **~187 kH/s** thanks to cooling

---

## Daily Energy Consumption

```
1500 mAh × 24 h = 36 000 mAh
```

At **5V voltage**

```
36 Ah × 5V = 180 Wh per day
```

---

## System Efficiency (~85%)

Power converters, powerbank modules and cables cause energy losses.

Estimated system efficiency:

```
≈ 85%
```

Real energy demand:

```
180 Wh ÷ 0.85 ≈ 212 Wh per day
```

So the system needs approximately:

```
≈ 212 Wh of energy per day
```

---

# Off-Grid Battery

![Offgrid](/imgs/offgird.jpg)

- 10 × **21700 lithium cells**
- Capacity per cell: **5000 mAh**

Total capacity:

```
10 × 5000 mAh = 50 000 mAh
```

- **7.5 A fuse**
- Powerbank module for voltage regulation

---

## Energy Stored in Batteries

At **3.7V nominal voltage**

```
50 000 mAh × 3.7V ≈ 185 Wh
```

Considering system efficiency:

```
185 Wh × 0.85 ≈ 157 Wh usable energy
```

---

# 36W Solar Panel

![SolarPanel](/imgs/solarpanel.jpg)

The solar panel has a **separate built-in energy storage module of 6000 mAh**.

This storage **is not permanently connected to the off-grid battery**.

To transfer energy:

- the storage module must be **physically connected with a cable**
- energy is **manually transferred to the off-grid battery**

---

## Solar Storage Capacity

Storage capacity:

```
6000 mAh
```

Usable energy considering system efficiency:

```
6000 mAh × 0.85 ≈ 5100 mAh
```

So one full charge cycle provides approximately:

```
≈ 5000 mAh of usable energy
```

---

# How Many Cycles Are Needed to Charge the Off-Grid Battery

Off-grid battery capacity:

```
50 000 mAh
```

Energy per solar storage cycle:

```
≈ 5000 mAh
```

Number of cycles needed:

```
50 000 mAh ÷ 5000 mAh ≈ 10 cycles
```

So approximately:

```
≈ 10 full solar storage charges
```

are required to fully charge the off-grid battery.

---

# Estimated Miner Runtime

Available energy in the off-grid battery:

```
≈ 157 Wh
```

Miner energy consumption:

```
≈ 212 Wh per day
```

Estimated runtime:

```
157 Wh ÷ 212 Wh ≈ 0.74 day
```

Which is approximately:

```
≈ 18 hours of mining
```

---

# System Diagram

```
        +----------------+
        |  36W Solar Panel |
        +----------------+
                 |
        +----------------+
        | 6000mAh Storage |
        +----------------+
                 |
        (manual cable transfer)
                 |
        +----------------+
        | Off-Grid 50k mAh |
        +----------------+
                 |
        +----------------+
        | Miner 3x ESP32 |
        +----------------+
```

---

# How I Use This System

The system does **not run continuously**.

Usage method:

- During the **week**, the solar panel **collects energy**
- The **6000 mAh storage module charges multiple times**
- Energy is **manually transferred to the off-grid battery**

After enough energy is collected:

- **on the weekend I start the miner**
- the miner runs **until the batteries are depleted**
