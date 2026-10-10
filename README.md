# Cooling Zone HVAC Design — Hindustan Unilever Case Study

A first-principles HVAC design for a food-processing cooling zone: bring a baked malt-based product from **80 °C to 40 °C in 10 minutes** without letting its **moisture rise above 2 %**.

Prepared for the Hindustan Unilever Limited (HUL) HVAC cooling-zone case competition.

| | |
|---|---|
| **Author** | Radha Gupta, IIT Delhi |
| **Domain** | Mechanical / HVAC, product and business-case design |
| **Deliverables** | 3-slide presentation ([PDF](docs/HUL_Cooling_Zone_Presentation.pdf)) and the original [problem statement](docs/Cooling_Zone_Problem_Statement.docx) |

---

## Solution at a glance

| Item | Result |
|---|---|
| Total cooling load | **128 kW = 36.4 TR** (including 15 % safety factor) |
| Specified capacity | **40 TR** (140.7 kW) chilled-water air handling unit (AHU) |
| Delivery method | Perforated **tunnel strip** blowing 8–10 m/s air directly onto the trays |
| Cooling time | **10 min** (limit: 10–12 min) |
| Supply air | 13 °C off-coil, dew point 11.2 °C |
| Chilled water | 6 °C → 12 °C, flow 18.4 m³/hr |
| CapEx | ≈ ₹36 lakh |
| Payback | ≈ 18 months |

---

## 1. Problem statement

A new food-processing facility needs a dedicated cooling zone. Baked product leaves the oven dry and hot and must be cooled to complete a phase transformation, **without picking up moisture**.

**Product and process**

| Parameter | Value |
|---|---|
| Product | Malt-based (wheat, malted barley, sugar) |
| Entry condition | 80 °C, ~2 % moisture |
| Exit target | 40 °C |
| Trays | Stainless steel, 800 × 1000 × 50 mm, open, 3 kg of product per tray |
| Throughput | 10 trays/min (0.5 kg/s) |

**Room**

| Parameter | Value |
|---|---|
| Size | 10 m × 20 m × 3 m |
| Walls | 200 mm concrete brick |
| Internal loads | 10 motors (6 × 3 kW + 4 × 5 kW) at 60 % load, 1 electrical panel, 10 operators |
| Door | 1 m × 2 m, open 30 s per opening |
| Ambient | 45 °C outside, 25 °C inside the room |
| Utility | Chilled water available at 6 °C; AHU sited next to the room |

**Required outputs:** HVAC system type and capacity, cooling load and chiller TR, and the ducting system that holds the room conditions.

**Hard constraints:** cooling cycle of 10 min minimum and 12 min maximum; product moisture must not increase.

![Room layout from the problem statement](assets/room-layout.png)

---

## 2. Approach

### 2.1 Thermal load (eight sources)

The moisture constraint drives every design choice, so the load was built up from first principles.

| Source | Basis | Load (kW) |
|---|---|---|
| Product | 0.5 kg/s × 1.85 kJ/kg·K × 40 K | 37.0 |
| Stainless-steel trays | 6 kg × 10/min (1.0 kg/s) × 0.50 kJ/kg·K × 40 K | 20.0 |
| Motors | 38 kW installed × 60 % | 22.8 |
| Roof transmission | U = 1.5, CLTD = 38 °C | 11.4 |
| Door infiltration | 4 openings/hr, 45 °C outside | 9.8 |
| Wall transmission | U = 1.8, CLTD = 22 °C | 7.1 |
| Electrical panel and people | | ≈ 3 |
| Safety factor | +15 % on all loads | 16.7 |
| **Total** | | **128.0** |

128 kW ÷ 3.517 = **36.4 TR**, rounded up to a **40 TR** unit.

![Slide 1: problem statement and thermal load](assets/slide-1-problem-statement.png)

### 2.2 System selection

Because moisture must stay at or below 2 %, three system families were ruled out: **evaporative, direct-spray and uncontrolled DX** cooling. The choice is a **chilled-water AHU** that cools *and* dehumidifies the supply air.

The delivery method matters as much as the plant. Plain room cooling cannot meet the cycle time; a tunnel strip can.

| Metric | Room cooling | Tunnel strip (chosen) |
|---|---|---|
| Air velocity | 0.2–0.5 m/s | 8–10 m/s |
| Convective coefficient *h* | ~8 W/m²K | ~35 W/m²K |
| Cooling cycle | 15–18 min (fails) | 10 min (passes) |
| Moisture control | Uncontrolled (fails) | Dehumidified (passes) |
| Target temperature met | Inconsistent | Guaranteed |

### 2.3 Air side and moisture control

Supply air volume follows from the sensible-heat equation:

```
V = Q / (ρ · Cp · ΔT) = 128 / (1.2 × 1.006 × 12) = 8.83 m³/s
```

Psychrometric state points show the air is dry enough to avoid condensation on the product:

| Point | Dry bulb | Humidity ratio |
|---|---|---|
| Outside | 45 °C | 30 g/kg |
| AHU off-coil (supply) | 13 °C | 8.3 g/kg (dew point 11.2 °C) |
| Room | 25 °C, ≤ 50 % RH | 9.9 g/kg |

The product surface stays at or above 40 °C, so there is no condensation risk. The room is held at **+20 Pa** positive pressure to keep humid outside air out.

### 2.4 Equipment and distribution

| Component | Specification |
|---|---|
| AHU | 40 TR chilled-water, fan + coil + filter, **VFD** on the fan motor |
| Chilled water | 6 °C supply, 12 °C return (6 °C ΔT), 18.4 m³/hr |
| CHW piping | 65 mm NB at 1.5 m/s |
| Main supply duct | GI, 600 × 400 mm, 5 m/s, 25 mm PUF insulation |
| Product zone | Perforated tunnel strip, 8–10 m/s, aimed directly at the trays |
| Conveyor | 10 trays/min, 3 kg/tray |

Product temperature steps down along the belt: **80 → 68 → 55 → 48 → 43 → 40 °C**.

![Slide 2: mechanical solution](assets/slide-2-mechanical-solution.png)

---

## 3. Business case

### 3.1 Capital cost

| Component | CapEx (₹ lakh) | Share |
|---|---|---|
| 40 TR chilled-water AHU | 18–20 | 51 % |
| GI insulated duct and tunnel strip | 8–10 | 25 % |
| CHW piping, valves and fittings | 3–4 | 9 % |
| Electrical, controls and BMS | 2–3 | 6 % |
| Civil works (pad and penetrations) | 1–2 | 4 % |
| VFDs on AHU motors (recommended) | 1.5–2 | 5 % |
| **Total** | **33.5–41** | 100 % |

### 3.2 Yield recovery and payback (conservative scenario)

| Metric | Value | ₹ lakh / year |
|---|---|---|
| Daily throughput | 28,800 kg/day (16 hr/day) | — |
| Maximum reject risk (1 % per day) | 288 kg/day lost | 142.6 |
| Required recovery (0.17 %) | 48.96 kg/day saved | 24.2 |
| Annual OpEx (fan + pump at ₹8/kWh) | — | −1.3 |
| **Net annual benefit** | | **≈ 22.9** |

**Payback = ₹36 lakh ÷ ₹22.9 lakh ≈ 18.8 months.**

The system pays for itself by recovering just **0.17 %** of product that would otherwise be rejected. Figures imply a product value of about ₹150/kg over 330 operating days a year.

### 3.3 Sustainability and implementation

- **Energy (Scope 2):** a chilled-water AHU cuts electrical draw by about 18 % versus a DX system.
- **Embodied carbon:** recyclable GI ductwork and a closed CHW loop, with no refrigerant venting or discharge.
- **Compliance:** HACCP and FSSAI aligned, removing product-recall liability from commissioning.
- **Rollout (90 days):** days 0–30 engineering and purchase orders; days 31–60 civil works and fabrication; days 61–90 AHU installation and a 72-hour test-adjust-balance (TAB) trial.

![Slide 3: business case](assets/slide-3-business-case.png)

---

## Repository structure

```
.
├── README.md
├── docs/
│   ├── HUL_Cooling_Zone_Presentation.pdf     # final 3-slide presentation
│   └── Cooling_Zone_Problem_Statement.docx   # original problem statement
└── assets/                                   # images used in this README
```

## Key assumptions

Product Cp 1.85 kJ/kg·K · stainless-steel Cp 0.50 kJ/kg·K · air density 1.2 kg/m³, Cp 1.006 kJ/kg·K · ambient 45 °C, 50 % RH · 16 operating hours/day, 330 days/year · electricity ₹8/kWh.

---

*Author: Radha Gupta, B.Tech, Indian Institute of Technology Delhi.*
