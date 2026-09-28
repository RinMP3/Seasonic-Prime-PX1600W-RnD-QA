# Seasonic Prime PX-1600W RnD & QA

---

## 1. Bill of Materials (BOM) & Component Breakdown

| Category | Component / Model | Specifications | Notes |
| :--- | :--- | :--- | :--- |
| **Primary Caps** | 2x Nippon Chemi-Con | 420V / 820 µF / 105°C | High-voltage APFC stage |
| **Primary Cap** | 1x Nippon Chemi-Con | 420V / 680 µF / 105°C | High-voltage APFC stage |
| **Secondary Cap** | 1x Nichicon | 16V / 2200 µF | Output filtering |
| **Main Transformers**| 2x VER42BB05 | 2307 W-D-B-B1 | Primary power delivery stage |
| **Aux Transformer** | 1x VEL22FB02 | 2248 W-I-B-A-I | Standby / auxiliary circuit |
| **Film Cap** | 1x Carli | AC/X2 safety rating | Line filtering |
| **Supervisor IC** | 1x Weltrend WT7527RA | Protection IC | OVP / UVP / OCP / SCP control |
| **Microcontroller**| 1x Weltrend WT51F104 | System MCU | System management & telemetry |

### Circuit Topology & PCB Architecture
* **Vertical Daughterboards:** The main PCB houses three vertically mounted daughterboards soldered directly to the main board. Two of these daughterboards communicate directly with each other via a dedicated **4-pin header**.
* **Galvanic Isolation:** Primary-to-secondary ground isolation measured `OL` (Open Loop), confirming full electrical isolation between circuits.
* **Transformer Secondary Windings:** Resistance across the VERA main transformer outputs measures between **0.2 Ω and 1.5 Ω**, confirming solid continuity and no winding breaks.

---

## 2. Connector Line Resistance Measurements

Static resistance readings taken directly on disconnected modular output sockets:

* **6-Pin Modular Connector:**
  * `+` Line: **62 kΩ**
  * Sense / Aux Line: **400 Ω**
* **8-Pin Modular Connector:**
  * `+` Lines: **60 kΩ to 65 kΩ**
* **24-Pin ATX Connector:**
  * Measured **9.5 kΩ**, **6.9 kΩ**, and **231 Ω** across respective rails.

---

## 3. Thermal Design & Extreme PCB Stress Testing

### Heat Dissipation Performance
* **Capacitor Thermal Transfer:** Under active heating of a large bulk capacitor, heat dissipation to the dedicated heatsink reached **53°C** against a **22°C ambient room temperature**, demonstrating excellent thermal coupling between PCB components and heatsinks.
* **Thermal Isolation & Spreaders:** The PCB incorporates multiple custom-molded thermal shields and isolation barriers, significantly improving passive thermal distribution across tight component clusters.

### Thermal Destruction & Textolite Stress Limits (Hot Air Rework)
Direct hot-air thermal stress tests performed without bottom preheating:

* **360°C Hot Air Test:**
  * **@ 01:16 (76s):** Solder mask bubbled.
  * **@ 01:53 (113s):** Green PCB solder mask darkened significantly.
  * **Engineering Insight:** The **1:16 threshold** proves that in the event of a localized component short-circuit, the textolite resists carbonization long enough to prevent inter-layer shorts and thermal runaway/fire.
  * **Safe Rework Window:** The safe point-heating window at **360°C** (without bottom preheat) is **45–50 seconds**. Exceeding this triggers rapid substrate degradation.
* **380°C Daughterboard Test:**
  * Extended hot air exposure at 380°C on the daughterboard during SMD component removal caused thermal shock, resulting in textolite swelling/bubbling due to prolonged airflow exposure.
* **400°C Overheating Test:**
  * Direct 400°C hot air exposure exceeding **30 seconds** caused structural failure of the board, resulting in severe textolite blackening.

---

## 4. Mechanical Design, Assembly & Ergonomics

### Disassembly & Chassis Improvements (PX-1600 vs. PX-1300)
* **Integrated AC Inlet Module:** Major RnD & Service upgrade — the AC power socket, main power switch, and Hybrid Fan mode switch are now consolidated into a single PCB module attached to the main board. On the PX-1300, the AC inlet block was built directly into the chassis frame as a single piece, making reassembly significantly harder.
* **Removable Modular Connector Panel:** Unlike the PX-1300 where the metal backplate with cable output pass-throughs was permanently fixed to the chassis, the modular socket panel on the PX-1600 is fully detachable. Removing this panel drastically eases both disassembly and PCB installation during reassembly.
* **Chassis Insulation Sheet:** Upgraded from the cheap transparent insulator on the PX-1300 to a sleek black insulation sheet inside the chassis casing. The main PCB front side also features a clean black finish.
* **Fan Grille Fasteners:** Chromed fan grille screws updated from proprietary/multi-point heads to standard Phillips screws. Cleaning the fan area on the PX-1600 is significantly easier.
* **Fastener Consistency:** Reassembly is foolproof — Seasonic used uniform screw threads and sizes throughout almost the entire chassis layout.
* **Tight Screw Access (Downside):** Due to denser component and heatsink placement, reaching certain main PCB mounting screws inside the chassis is more awkward than on lower-wattage units.

### Thermal Interface Materials (TIM) & Insulation
* **Mylar Sheet Bonding:** An additional thermal pad was added between the PCB and the bottom Mylar sheet, causing the Mylar insulator to come off bonded to the PCB during disassembly.
* **Chassis Heat Transfer Pad:** The main thermal pad transferring heat from the PCB to the metal enclosure has been made thicker and wider.

### Accessories & Packaging
* **Sleeved Cabling:** All modular cables are now fully sleeved.
* **Cable Storage:** Cable pouch upgraded from a basic drawstring bag to a heavy-duty ziplock storage bag.
* **Bundled Accessories:** Included PSU tester block and 90-degree 24-pin motherboard adapter function at 100% efficiency and fit cleanly.

---

## 5. Serviceability & Repairability Analysis

### The Glue / Compound Issue (Over-Application)
* **Excessive Compound:** Seasonic applied a **massive amount of structural adhesive/silicone** internally — significantly more than in previous revisions.
* **Serviceability Impact:** Over-gluing severely hinders component desoldering, blocks trace visibility, and complicates diagnosing trace burnouts or localized board shorts.

### SMD Desoldering Rules
* **Hot Air Mandatory:** SMD components on the main PCB are easy to desolder **ONLY** with a hot-air rework station.
* **Soldering Iron Warning:** Attempting SMD removal using a soldering iron alone is impossible due to the PCB's massive copper ground planes and thermal mass. Personal testing confirmed **torn PCB solder pads** when relying solely on an iron.
* **HV Capacitor Replacement:** Replacing the high-voltage primary caps is achievable using an **80W+ soldering iron combined with hot air**, provided all detachable main PCB heatsinks are removed first to prevent thermal sinking.

### Solder Quality & Inlet Mesh
* **Solder Joints:** A few minor, untidy solder joints were identified on the main board (minority). Overall topology and tight packing favor performance and thermals, but compromise repairability.
* **AC Inlet Mesh Adhesive:** The protective mesh lining on the AC power input block is poorly adhered; the adhesive base requires better quality control.

---

## 6. Engineering Feedback & Recommendations for Seasonic R&D / QA

1. **Reduce Internal Silicone Application:** Tone down the excessive glue application. It creates severe headaches for QA auditing, warranty repairs, and component tracing.
2. **Upgrade AC Inlet Mesh Adhesive:** Re-evaluate the sticky backing formula used for securing the power inlet protective screen.
3. **Tamper-Evident Warranty Seals:** Upgrade the warranty stickers. While current stickers are brittle to tool contact, they can still be peeled off cleanly without leaving a `VOID` residue pattern, allowing clean tampering.
4. **Accessory Aesthetics:** Update the included sticker pack aesthetics — introducing subtle blue accents alongside the standard silver/black design would better complement modern build themes. Or add cute small pin with Watty :)

---

> [!NOTE]
>  This entire audit was compiled directly on a mobile phone, as my primary PC failed and I had to sell the remaining working components to fund a future build.


<details>
  <summary><b> Photo Gallery </b></summary>
  <br>
<img width="3337" height="1747" alt="image" src="https://github.com/user-attachments/assets/84239997-3cd7-4706-93b3-0a24f09113fc" />
<img width="3354" height="1756" alt="image" src="https://github.com/user-attachments/assets/593d43be-304d-4e6a-9dd3-cc9a5497e982" />
<img width="3926" height="2055" alt="image" src="https://github.com/user-attachments/assets/18ab8305-8e75-49a1-910e-5d9ae6b25bad" />
<img width="4032" height="2111" alt="image" src="https://github.com/user-attachments/assets/534670f2-a805-4d9b-bf88-d2db6259426e" />
<img width="4032" height="2111" alt="image" src="https://github.com/user-attachments/assets/376bd6bf-cebb-4efb-9437-4d4f1445af82" />
<img width="4032" height="2111" alt="image" src="https://github.com/user-attachments/assets/6efce894-8119-4745-b1f2-fd97aa2c5481" />
<img width="4032" height="2111" alt="image" src="https://github.com/user-attachments/assets/1bdd9351-5b32-4c2e-a2b8-df1608df83bf" />
<img width="4032" height="2111" alt="image" src="https://github.com/user-attachments/assets/634c91ce-274b-4e10-b27e-99b55c909a82" />
<img width="3835" height="2008" alt="image" src="https://github.com/user-attachments/assets/6edc331c-a475-435e-9e90-66a17f9475e4" />
<img width="4032" height="2111" alt="image" src="https://github.com/user-attachments/assets/044093a9-4f3b-4600-92dc-e05e14a89ef8" />
<img width="4032" height="2111" alt="image" src="https://github.com/user-attachments/assets/818f94ab-4283-4a01-9551-568fbe5a5f44" />
<img width="4032" height="2111" alt="image" src="https://github.com/user-attachments/assets/70a07e75-e7fd-4450-b628-90def2175e48" />
<img width="3460" height="1812" alt="image" src="https://github.com/user-attachments/assets/42242887-b7a0-4d46-8183-a603cd703a8e" />
<img width="4032" height="2111" alt="image" src="https://github.com/user-attachments/assets/027d179d-beb7-47c0-9025-2cd1fdfd678f" />
<img width="1737" height="909" alt="image" src="https://github.com/user-attachments/assets/536d4371-1ae7-4ccb-b65a-59487474c50a" />
<img width="2051" height="1074" alt="image" src="https://github.com/user-attachments/assets/b7bdfbf7-8aaa-40f4-93eb-0d3b952dfbf8" />
<img width="4032" height="2111" alt="image" src="https://github.com/user-attachments/assets/a5942863-8429-48ed-8e5d-19e9199312cb" />
<img width="4032" height="2111" alt="image" src="https://github.com/user-attachments/assets/c1031b67-e6bf-4f29-a38d-070bf323ad29" />
<img width="3141" height="1644" alt="image" src="https://github.com/user-attachments/assets/fff207ed-826f-41a2-96cb-8e9d3f70275f" />
<img width="2652" height="1388" alt="image" src="https://github.com/user-attachments/assets/040bcb6d-f0d1-48fe-a730-967404045a71" />
<img width="2135" height="1118" alt="image" src="https://github.com/user-attachments/assets/91436eed-3043-4764-8bef-3a35b12e74c8" />
<img width="4032" height="2111" alt="image" src="https://github.com/user-attachments/assets/f8bc9da0-aa85-41c6-a709-a17d2b786b65" />
<img width="4032" height="2111" alt="image" src="https://github.com/user-attachments/assets/c4c7cca9-5ba9-4fa2-bc10-86a276b03000" />
<img width="4032" height="2111" alt="image" src="https://github.com/user-attachments/assets/79f2b0b4-35f4-483f-87ec-43ea9f1f0ce2" />
<img width="4032" height="2111" alt="image" src="https://github.com/user-attachments/assets/fcfa6f73-cfe7-4231-b51a-8eb3a93e967a" />
<img width="2488" height="1303" alt="image" src="https://github.com/user-attachments/assets/b169c6af-599c-4a1d-b411-874d6396a4c2" />
<img width="3664" height="1918" alt="image" src="https://github.com/user-attachments/assets/bda3c25a-017b-43dc-a75c-c5b0a4df8d64" />
<img width="3326" height="1741" alt="image" src="https://github.com/user-attachments/assets/e464cee4-f8d3-4341-b7e1-1b15b8ab2d01" />
<img width="4032" height="2111" alt="image" src="https://github.com/user-attachments/assets/fdfbab29-ac20-489f-91b1-9ea7303ee046" />
<img width="4032" height="2111" alt="image" src="https://github.com/user-attachments/assets/f4f48065-810b-4c9a-915d-188f6e5c361e" />
<img width="3024" height="1583" alt="image" src="https://github.com/user-attachments/assets/abfea2a2-7832-42fc-a1ed-5c96971b3451" />
<img width="4032" height="2111" alt="image" src="https://github.com/user-attachments/assets/74af1e28-afb6-4269-9a87-691ccd33629a" />
<img width="4032" height="2111" alt="image" src="https://github.com/user-attachments/assets/7e392088-d3e0-4bc5-8d34-ae9915be1cf4" />

  </details>
