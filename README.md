# EVOP-V2G Dataset

This repository contains the integrated datasets and experimental configurations used to evaluate the **EVOP-V2G** framework. The data integrates real-world ride-sharing trip statistics from Melbourne, Australia, with PlugShare charging infrastructure and Australian Time-of-Use (TOU) energy tariffs.

---

## 📂 Dataset Hierarchy

We provide two scales of instances to support both exact Mixed-Integer Programming (MIP) solvers and heuristic approaches like Large Neighborhood Search (LNS) and Evolutionary Algorithms (EA).

### 1. Small-Scale Instances 
Due to the scalability limitations of MIP models, these instances are designed for performance comparison on a manageable scale.
* **Orders:** 30 randomly sampled orders per instance.
* **Charging Stations:** 3 total (the EV owner’s home + 2 randomly selected candidates).
* **Source/Destination:** Identical location, randomly selected within the bounding box of the specific order set (EV owner's home).
* **Iteration:** 10 unique instances are generated for statistical reliability.

### 2. Large-Scale Instances 
Designed to assess the relative performance of LNS and EA against baseline models.
* **Orders:** 900 randomly sampled orders.
* **Charging Stations:** Full set of 70 validated Melbourne stations.
* **Source/Destination:** Identical location, randomly selected within the bounding box of the specific order set (EV owner's home).
* **Iteration:** 10 unique instances are generated for each order-candidate variation.

---

## 🛠 Experimental Variations

The dataset facilitates sensitivity analysis across three primary dimensions. Experiments vary one criterion at a time while keeping the others fixed at their **Default** values.

| Dimension | Variations | Default Value |
| :--- | :--- | :--- |
| **Bounding Box** | 10%, 40%, 70%, 100% (of Melbourne Metro) | **40%** |
| **Ride Length** | 5–10 km, 10–25 km, > 25 km | **10–25 km** |
| **Time Window** | 2h (9–11 am), 5h (9 am–2 pm), 8h (9 am–5 pm) | **8h** |

---

## 🔋 Battery & EV Specifications

To reflect real-world heterogeneity in EV models, we evaluate performance across three representative battery capacities:

* **40 kWh:** (e.g., Nissan Leaf)
* **70 kWh:** (e.g., Tesla Model S) — **Default**
* **108 kWh:** (e.g., Mercedes-Benz EQS SUV)

### Standard Operational Parameters:
* **Driving Efficiency ($\gamma$):** 0.175 kWh/km (Capacity/Range ratio).
* **Home Charging Rate:** 7 kW.
* **Working Hours:** 9:00 AM ($\tau^s_w$) to 5:00 PM ($\tau^e_w$).
* **State of Charge (SoC):** Initial $B_s = 100\%$; Minimum required at destination $B_d = 0\%$.

---
