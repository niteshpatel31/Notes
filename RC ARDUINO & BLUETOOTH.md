![[Drawing 2026-07-19 23.01.10.excalidraw]]

# Arduino Bluetooth RC Car Wiring

```text
                          +----------------------+
                          |      Arduino UNO     |
                          |                      |
                          | D2  ------------------------ IN1
                          | D3  ------------------------ IN2
                          | D4  ------------------------ IN3
                          | D7  ------------------------ IN4
                          | D5 (PWM) ------------------- ENA
                          | D6 (PWM) ------------------- ENB
                          |                      |
                          | 5V ------------------------ HC-05 VCC
                          | GND ----------------------- HC-05 GND
                          | D10 <---------------------- HC-05 TXD
                          | D11 ----------------------> HC-05 RXD
                          |           (Voltage Divider Recommended)
                          +----------------------+
                                      |
                                      |
                                  Common GND
                                      |
                                      |
        +---------------------------------------------------+
        |                     L298N                         |
        |                                                   |
Battery + ---------- +12V                           OUT1 -------- Left Motor +
Battery - ---------- GND                            OUT2 -------- Left Motor -
                     |                              OUT3 -------- Right Motor +
                     |                              OUT4 -------- Right Motor -
                     +-----------------------------------------------+
```

---

## HC-05 Connections

| HC-05 | Arduino UNO |
|--------|-------------|
| VCC | 5V |
| GND | GND |
| TXD | D10 |
| RXD | D11 (through voltage divider) |

---

## L298N Connections

| L298N | Arduino UNO |
|--------|-------------|
| ENA | D5 (PWM) |
| IN1 | D2 |
| IN2 | D3 |
| IN3 | D4 |
| IN4 | D7 |
| ENB | D6 (PWM) |
| GND | GND |
| +12V | Battery + |

---

## Motor Connections

```
OUT1 ───────── Left Motor +

OUT2 ───────── Left Motor -

OUT3 ───────── Right Motor +

OUT4 ───────── Right Motor -
```

---

## 4WD Wiring

```
             OUT1
               |
      +--------+--------+
      |                 |
 Front Left       Rear Left

             OUT2
               |
      +--------+--------+
      |                 |
 Front Left       Rear Left
```

```
             OUT3
               |
      +--------+--------+
      |                 |
 Front Right      Rear Right

             OUT4
               |
      +--------+--------+
      |                 |
 Front Right      Rear Right
```

(Connect the motors on each side in **parallel**.)

---

## Battery Wiring

```
Battery +
     |
     +------ Switch ------> L298N +12V

Battery -
     |
     +--------------------> L298N GND
     |
     +--------------------> Arduino GND
```

---

## Power Notes

- ❌ Do **not** power the motors from the Arduino.
- ❌ Do **not** use a rectangular 9V battery.
- ✅ Recommended battery:
  - 2 × 18650 Li-ion (7.4V)
  - 6 × AA batteries
  - 2S LiPo

---

## Pin Summary

| Arduino | Connected To |
|----------|--------------|
| D2 | L298N IN1 |
| D3 | L298N IN2 |
| D4 | L298N IN3 |
| D5 | L298N ENA |
| D6 | L298N ENB |
| D7 | L298N IN4 |
| D10 | HC-05 TXD |
| D11 | HC-05 RXD |
| 5V | HC-05 VCC |
| GND | HC-05 GND + L298N GND |


# Our connection
## Arduino -> Bluetooth module
GND -> GND
5V -> VCC
RX -> TX
TX -> RX 

## Arduino -> Motor Driver
10 ->  
11 -> 
12 -> 
13 -> 

## Battery -> Motor Driver -> Arduino
vin ports are involved 