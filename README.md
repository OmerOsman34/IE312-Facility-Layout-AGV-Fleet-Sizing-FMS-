# IE312 — Facility Layout & AGV Fleet Sizing (FMS)

This repository contains my IE312 (Facility Design & Planning) project for a hypothetical Flexible Manufacturing System (FMS).  
The project has two parts:
1) Facility layout design using constructive + improvement heuristics  
2) AGV fleet sizing using four analytical methods proposed by Egbelu (1987)

## Part I — Facility Layout Design
### Goal
Design two sensible layout alternatives for the given workstations and a Central Buffer (CB), and compare them based on total transportation cost.

### Method
- Prepared **From–To flow** and **shortest-path distance** matrices between pick-up (P) and delivery (D) nodes.
- Converted flow intensity and utilization importance into **closeness ratings**, then computed **Total Closeness Ratings (TCR)** for placement priority.
- Generated an initial layout with a **constructive heuristic** using **Weighted Placement Value (WPV)**.
- Improved the layout with an **adjacent-interchange improvement heuristic**:
  - Tested feasible swaps (adjacent departments)
  - Recomputed transportation cost (Flow × Distance) for each swap
  - Kept the best layout until no further improvement was possible

### Key Result
- Total transportation cost improved from **1908** (constructive layout) to **1476** after the best interchange, and then converged (no better swap found).

## Part II — AGV Fleet Sizing (Egbelu, 1987)
### Goal
Estimate the required number of AGVs to satisfy the system’s daily material handling demand without running a simulation.

### Method
Calculated the fleet size using **four analytical methods** from Egbelu (1987), incorporating:
- AGV speed, pick-up & delivery times
- Daily availability with charging time
- Efficiency factor
- Operational interferences (blocking / idleness) where applicable
- Loaded and empty travel distances (directional travel)

### Key Result
- Different assumptions lead to estimates ranging from **4 to 7** AGVs.
- A robust recommendation of **7 AGVs** was selected to ensure stable operation under variability.

## Repository Structure (suggested)
- `reports/`
  - `IE 312 Proje Part 1 Report 2025.pdf`
  - `IE 312 Proje-Part2 Report 2025.pdf`
- `spreadsheets/`
  - `IE312 Part 1.xlsx`
  - `IE312 Part 2.xlsx`
- `assignment/`
  - `IE 312 - Project Part I Description.pdf/.docx`
  - `IE312 - Project Part II Description.pdf`
- `references/`
  - `Egbelu Paper For Project Part II.pdf`

## How to Reproduce
1) Open the Excel files in `spreadsheets/`:
   - Part I: flow/distance matrices, TCR/WPV calculations, improvement iterations
   - Part II: fleet size calculations for Methods 1–4
2) See `reports/` for the written explanation, assumptions, and final decisions.

## Reference
Egbelu, P. J. (1987). *The use of non-simulation approaches in estimating vehicle requirements in an automated guided vehicle-based transport system.* Material Flow, 4, 17–32.
