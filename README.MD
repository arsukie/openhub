# OpenHub

An open-source USB 2.0 hub. USB-C in, 4 ports out (2x USB-C, 2x USB-A)

> schematic's done, PCB is routed, board's off to fab. what could go wrong

## What it is

- USB 2.0 High-Speed (480 Mbps), running on a CoreChips **SL2.1A** hub controller (SOP-16)
- USB-C upstream (USBC1) - configured as a **sink** via 5.1kΩ CC pull-downs (Rd), so it correctly IDs as a device drawing power
- 2x USB-C downstream (USBC2, USBC3) - configured as **sources** via 56kΩ CC pull-ups (Rp), advertising default USB power out
- 2x USB-A downstream, wired straight off the controller's remaining data channels
- **SY6280AAC** current-limited power switch (U1) on the power path, current limit set via a 4.7kΩ ISET resistor (R8) - so a bad downstream device doesn't take the whole hub down with it
- EN pin on the power switch tied directly to VBUS, so downstream power just turns on the moment the hub gets plugged in, no extra logic needed
- Status LED with a 1kΩ series resistor because a silent hub is a suspicious hub
- 12MHz crystal + 15pF load caps for the controller clock
- 10µF / 100nF decoupling pairs at every rail (VDD18/VDD33/VDD5) and at each port, because unstable rails are how you get a board that works on your desk and nowhere else

## Status
Schematic + routing: done.

# Bill of Materials
 
## Selected Parts (12 items)
 
| Part Detail | Selected by | Top Designator | Qty | Source | Ext. Price |
|---|---|---|---|---|---|
| CL21A106KAYNNNE (Basic, C15850) | System | C10,C11,C12,C13... | 10 | JLCPCB | $0.9600 |
| TYPE-C-31-M-12 (Extended, C165948) | System | USBC1,USBC2,USB... | 6 | JLCPCB | $1.1136 |
| SL2.1A (Extended, C6798314) | Customer | U2 | 2 | JLCPCB | $0.5086 |
| 0603WAF5101T5E (Basic, C23186) | System | R1,R2 | 4 | JLCPCB | $0.0100 |
| CL10A106MA8NRNC (Basic, C96446) | System | C1,C2 | 4 | JLCPCB | $0.3168 |
| SY6280AAC (Extended, C55136) | System | U1 | 5 | JLCPCB | $0.4795 |
| HoLTT0603-1/10W-4.7K-1% (Extended, C2904521) | System | R8 | 6 | JLCPCB | $0.2310 |
| USB-231-ARY (Extended, C720525) | System | USB1,USB2 | 4 | JLCPCB | $0.7768 |
| A-SP192DGHC-C01-4T (Extended, C19171301) | System | LED1 | 20 | JLCPCB | $0.5600 |
| CC0603KRX7R9BB104 (Basic, C14663) | System | C5,C6,C7,C8,C9,... | 14 | JLCPCB | $0.2100 |
| RC0805FR-071KL (Extended, C95781) | System | R7 | 20 | JLCPCB | $0.1140 |
| CL10C150JB8NNNC (Basic, C1644) | System | C3,C4 | 4 | JLCPCB | $0.0556 |
 
## PCB & Shipping
 
| Type | Item | Description | Qty | Build Time | Price |
|---|---|---|---|---|---|
| PCB | Gerber_PCB1_2026-08-09_Y6 | PCB prototype: Y6-13163216A, Black, 1.6 Thickness, HASL(with lead) | 5 pcs | 24 hours | $4.00 |
| PCBA | Gerber_PCB1_2026-08-09_Y6 | Economic PCBA: SMT026080960460-13163216A, Assemble top side | 2 pcs | 2 - 3 days | $39.07 |
| PCB | Gerber_PCB1_2026-08-16_Y8 | PCB prototype: Y8-13163216A, Green, 1.6 Thickness, HASL(with lead) | 5 pcs | 3 - 4 days | $7.00 |
 
| | |
|---|---|
| **PCB (Merchandise)** | $50.07 |
| Shipping | $18.21 |
| **Subtotal** | **$68.28** |

## Cart


## Milestones

1. Design finalization - schematic + routing done



Built by **Arjun Khanal** @aruskie
