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


## Bill of Materials

| Designator(s) | Part | Qty | Package | Ext. Price |
|---|---|---|---|---|
| U2 | SL2.1A - USB 2.0 4-port hub controller | 1 | SOP-16 | $0.5060 |
| U1 | SY6280AAC - current-limited power/load switch | 1 | SOT | $0.4770 |
| USBC1, USBC2, USBC3 | TYPE-C-31-M-12 USB-C connector (1 upstream, 2 downstream) | 3 | USB-C THT | $1.1082 |
| USB1, USB2 | USB-231-ARY USB-A downstream connector | 2 | USB-A THT | $0.7728 |
| R1, R2 | 5.1kΩ resistor - CC pull-down (Rd, upstream sink config) | 2 | 0603 | $0.0336 |
| R3, R4, R5, R6 | 56kΩ resistor - CC pull-up (Rp, downstream source config) | 4 | 0603 | included |
| R7 | 1kΩ resistor - status LED | 1 | 0805 | $0.1120 |
| R8 | 4.7kΩ resistor - ISET current-limit set | 1 | 0603 | $0.2304 |
| LED1 | Status LED | 1 | SMD | $0.5580 |
| C1, C2 | 10µF ceramic capacitor (rail decoupling) | 2 | 0805 | $0.3280 |
| C10–C14 (approx.) | 10µF ceramic capacitor (per-port decoupling) | 5 | 0805 | $1.0460 |
| C5–C9 (approx.) | 100nF ceramic capacitor (decoupling) | 7 | 0603 | $0.2660 |
| C3, C4 | 15pF ceramic capacitor (crystal load caps) | 2 | 0603 | $0.0552 |
| X1 | 12MHz crystal | 1 | HC-49US | included |

Some low-value passive designators are grouped/approximate - JLCPCB's BOM quote UI truncated the full designator list, so `C10–C14` and `C5–C9` are best-effort groupings, not gospel.

## Budget

| Item | Qty | Build Time | Price |
|---|---|---|---|
| Bare 4-layer PCB - unassembled variant (green, 1.6mm, HASL w/ lead) | 5 | 3–4 days | $7.00 |
| Bare 2-layer PCB - main hub board (black, 1.6mm, HASL w/ lead) | 5 | 24 hours | $4.00 |
| PCBA - 2-layer board, Economic assembly, top side | 5 | 2–3 days | $47.25 |
| **Merchandise total** | | | **$58.25** |
| Shipping | | | $36.87 |
| **Subtotal** | | | **$95.12** |

Straight off the JLCPCB cart, nothing padded on top. Total order weight: 0.57kg.

## Schematics
[Schematic](Schematic.png)
<img herf = "Schematic.png">

### 3D View
[3D_view](3D_view.png)

## Milestones

1. Design finalization - schematic + routing done



Built by **Arjun Khanal** @aruskie
