# Duino-Coin Solar Miner Project
## Opis Projektu

Projekt składa się z:

1. Miner oparty na ESP32-WROOM
2. Off-grid z akumulatorami 21700
3. Panel słoneczny 36 W z osobnym magazynem energii

Celem projektu jest kopanie Duino-Coin w sposób energooszczędny i niezależny od sieci elektrycznej.

---

# Miner

![Miner](/imgs/miner.jpg)

- 3 moduły **ESP32-WROOM**
- Wentylator **5V** dla chłodzenia
- Średnie zużycie: **1500 mAh/h**
- Wydajność: **~1.14 Duino-Coin/h**
- Stabilna praca: **~187 kH/s** dzięki chłodzeniu

---

## Zużycie energii dziennie

```
1500 mAh × 24 h = 36 000 mAh
```

Przy napięciu **5V**

```
36 Ah × 5V = 180 Wh dziennie
```

---

## Uwzględnienie sprawności systemu (~85%)

Przetwornice, moduły powerbank oraz przewody powodują straty energii.

Zakładamy sprawność:

```
≈ 85 %
```

Realne zapotrzebowanie energii:

```
180 Wh ÷ 0.85 ≈ 212 Wh dziennie
```

---

# Off-Grid

![Offgrid](/imgs/offgird.jpg)

- 10 ogniw **21700**
- Pojemność jednego ogniwa: **5000 mAh**
- Łączna pojemność:

```
10 × 5000 mAh = 50 000 mAh
```

- Bezpiecznik: **7.5 A**
- Moduł powerbank do regulacji napięcia

---

## Energia w akumulatorach

Przy napięciu ogniw **3.7V**

```
50 000 mAh × 3.7V ≈ 185 Wh
```

Po uwzględnieniu sprawności systemu:

```
185 Wh × 0.85 ≈ 157 Wh użytecznej energii
```

---

# Panel Słoneczny 36 W

![SolarPanel](/imgs/solarpanel.jpg)

Panel posiada **osobny magazyn energii 6000 mAh**.

Ten magazyn nie jest połączony na stałe z off-gridem.  
Aby naładować off-grid należy **ręcznie podłączyć magazyn kablem** i przenieść energię.

---

## Pojemność magazynu panelu

Magazyn:

```
6000 mAh
```

Realnie użyteczna energia (sprawność 85%):

```
6000 mAh × 0.85 ≈ 5100 mAh
```

Czyli jeden pełny cykl magazynu daje około:

```
≈ 5000 mAh energii
```

---

# Ile cykli potrzeba aby naładować Off-Grid

Off-grid:

```
50 000 mAh
```

Energia z jednego magazynu panelu:

```
≈ 5000 mAh
```

Liczba cykli ładowania:

```
50 000 mAh ÷ 5000 mAh ≈ 10 cykli
```

Czyli potrzeba około:

```
≈ 10 pełnych ładowań magazynu panelu
```

aby naładować cały off-grid.

---

# Szacowany czas pracy minera

Dostępna energia w off-grid:

```
≈ 157 Wh
```

Zużycie minera:

```
≈ 212 Wh / dzień
```

Czas pracy:

```
157 Wh ÷ 212 Wh ≈ 0.74 dnia
```

Czyli około:

```
≈ 18 godzin pracy
```

---

# Diagram Systemu

```
        +----------------+
        |  Panel 36W     |
        +----------------+
                 |
        +----------------+
        | Magazyn 6000mAh|
        +----------------+
                 |
      (ręczne podłączenie)
                 |
        +----------------+
        | Off-Grid 50k mAh|
        +----------------+
                 |
        +----------------+
        | Miner 3x ESP32 |
        +----------------+
```

---

# Jak korzystam z systemu

System nie pracuje ciągle.

Sposób używania:

- w **tygodniu panel słoneczny zbiera energię**
- magazyn **6000 mAh ładuje się wiele razy**
- energia jest **przenoszona do off-gridu**

Po zebraniu energii:

- **w weekend uruchamiam minera**
- koparka działa aż do rozładowania akumulatorów
