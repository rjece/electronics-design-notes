
# Component Attribute Standardization Guide
## Autodesk Fusion Electronics

This document outlines the standardized attribute framework for professional engineering documentation, procurement, and assembly.

---

#Note:
The following are attributes that can be added to components in Fusion Electronics. 
In Fusion, every component has two "System Properties" that always exist:
- NAME: This is the Designator (e.g., R1, C10, U1). You put the part's "address" here.
- VALUE: This is the Basic Spec (e.g., 10k, 100nF). You put the primary magnitude here.
Anything else (Power, Voltage, DNP status) is a Custom Attribute that you add manually.

### 1. Essential Metadata (Physical & Electrical Identity)
These attributes define what the part is beyond its magnitude.

| Attribute Name | Example Value | Purpose |
| :--- | :--- | :--- |
| **MPN** | `GRM188R61A106KE` | **Manufacturer Part Number.** Unique ID for exact procurement. |
| **PACKAGE** | `0603`, `SOT-23` | Defines the physical footprint and PCB landing pattern. |
| **TYPE** | `X7R`, `Thin Film` | Defines material technology (dielectric, composition, etc.). |
| **RATING** | `25V`, `0.25W` | Defines electrical limits (Voltage for caps, Power for resistors). |

---

### 2. Assembly & Logistics
Attributes used to communicate intent to the assembly house or purchasing manager.

| Attribute Name | Example Value | Purpose |
| :--- | :--- | :--- |
| **POPULATE** | `POP`, `DNP` | **POP** (Populate) or **DNP** (Do Not Populate/Install). |
| **SUBSTITUTE** | `EXACT`, `CE`, `EQUIV` | Defines the logic for finding alternative parts. |
| **MPN_ALT** | `ERJ-3EKF1002V` | A specific "Plan B" part number if the primary is unavailable. |

---

### 3. Substitution Logic (The "SUBSTITUTE" Vocabulary)
Use these shorthand codes to maintain design integrity during procurement:

* **EXACT**: No changes allowed. Essential for MCUs, RF chips (LoRa), and precision sensors.
* **CE (Close Equivalent)**: **Equal or Better** specs only. Allows higher voltage or tighter tolerance, but the **footprint must be identical**.
* **EQUIV (Equivalent)**: Standard parts. Any part matching the basic specs is acceptable (common for generic pull-ups).

---

### 4. Implementation Workflow
1.  **Library Level**: Add these names as blank placeholders in `.flbr` files.
2.  **Schematic Level**: Use the **Inspector** for batch updates or `attrib-edit.ulp` for a master table view.
3.  **BOM Export**: Ensure these custom columns are enabled in the BOM dialog before exporting to CSV/Excel.

---
*Optimized for professional engineering documentation and PECE candidacy standards.*
