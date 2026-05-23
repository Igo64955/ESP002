# ESP002

## Schaltplan: ESP8266MOD-12-F mit 5V-Versorgung

```text
5V Eingang
  │
  ├─[100µF]─ GND
  │
  └── VIN ┌────────────────────┐
          │ 3.3V-Regler        │ (z. B. AMS1117-3.3)
GND ──────┤ GND            VOUT├─────────────── 3V3-Schiene
          └────────────────────┘
                             │
                       [10µF]│
                             ├─ GND
                             │
3V3-Schiene ─────────────────┼──────── VCC (ESP8266MOD-12-F, Pin 8)
                             ├──────── CH_PD / EN (Pin 3) über 10k an 3V3
                             ├──────── RST (Pin 32) über 10k an 3V3
                             ├──────── GPIO0 (Pin 25) über 10k an 3V3
                             ├──────── GPIO2 (Pin 24) über 10k an 3V3
                             └──────── GPIO15 (Pin 23) über 10k an GND

GND ──────────────────────────┬──────── GND (ESP-Pins 9, 15, 31)
                              └──────── gemeinsame Masse

USB-UART TX ───────────────────────────── RXD0 / GPIO3 (Pin 21)
USB-UART RX ───────────────────────────── TXD0 / GPIO1 (Pin 22)
USB-UART GND ──────────────────────────── GND

Optional:
- Taster FLASH: GPIO0 nach GND (für Programmiermodus)
- Taster RESET: RST nach GND
```

### Hinweise

- ESP8266MOD-12-F arbeitet nur mit **3,3V** an VCC (niemals direkt 5V).
- Der 3,3V-Regler sollte genügend Strom liefern (empfohlen mindestens 500mA).
- Für stabile Versorgung sind Abblockkondensatoren nahe am Modul wichtig.
